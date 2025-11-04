## Builder Data Loading App

This script loads Excel or CSV files from the Advana External Data Load (EDL) site into a specified table. The data is then available for use within the Advana platform, accessible via SQL queries or a Python notebook in Databricks for further processing. Only builder data is supported. Enterprise data is not supported with this script.

The application includes robust input checks and provides feedback for errors. If an issue prevents the data load from completing, an error will be displayed, and the program will cease execution.

***

### How to Use

1.  **Upload** your CSV or Excel file to the Advana External Data Load (EDL) site under the `Builder Data` location.
    * Only `.xlsx` (Excel) or `.csv` files are supported.

2.  **Wait** until `COMPLETED` appears in the `Status` field on the Advana EDL site. This may take a while. You may need to refresh the page to see the status update.

3.  **Copy** the entire `Key` field for the file you uploaded to Advana EDL and paste it into the `Key (from Advana EDL)` field.
    * Can't see the `Key (from Advana EDL)` field? This means the widgets haven't loaded. Press the `Run all` button at the top right. You will then see widgets at the top of the script where you can enter the key.

4.  **Select** either `Overwrite` or `Append` based on your needs.
    * **Warning:** Selecting `Overwrite` will delete all previous data in the table.

5.  **Enter** the number of rows you want to skip. This is useful for skipping empty or title rows in your file.

6.  **Enter** the desired table name for your data.
    * Ensure you enter the correct table name before running the application.

7.  **Click** `Run all`.

***

### Results

1)  **Success:** Every cell of code will run and the last cell will have a ✅ green check mark.
    * The key and target schema and table name will be listed.
    * The data is now ready for further processing.
2)  **Failure:** There will be a cell that failed.
    * Failure can easily be seen by a red rectangle on the right side. Click the red rectangle to be taken to the cell and view the error message.
    * The failed cell can also be found by scrolling to the cell.
    * Follow the instructions of the error message to resolve the issue.

***

### Notes

* This program only reads the _first sheet_ of an Excel file. Make sure your data is on the first sheet.
* The program automatically removes any empty columns.
* If `Skip Rows` is not specified, the script will not skip any rows.
* Column names are automatically renamed to a Databricks-compatible format. Specifically, the program:
    * Changes the name to all uppercase.
    * Replaces spaces, slashes, and periods with underscores.
    * Removes other invalid characters as defined by [Databricks](https://docs.databricks.com/aws/en/sql/language-manual/sql-ref-names).

***

Created by Noel Mrowiec  
github.com/noelmrowiec
10/1/202