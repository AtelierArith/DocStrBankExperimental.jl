```
write_gsheet(data::DataFrame, spreadsheet_id::String; sheet::String="Sheet1", range::String="", missing_value::String = "", append::Bool = true)
```

Writes the contents of a DataFrame to a specified Google Sheets spreadsheet.

# Arguments

  * `data::DataFrame`: The DataFrame containing the data to be written to Google Sheets.
  * `spreadsheet_id::String`: The ID of the Google Sheets spreadsheet or the full URL containing the ID.
  * `sheet::String`: The name of the sheet within the spreadsheet where the data will be written. Defaults to "Sheet1".
  * `range::String`: The range in the sheet where the data will be written. If empty, defaults to "A1".
  * `missing_value::String`: The value to replace missing entries in the DataFrame. Defaults to an empty string.
  * `append::Bool`: If true, appends the data to the existing data in the sheet. If false, overwrites the existing data. Defaults to true.

# Examples

```
julia> df = DataFrame(A=1:5, B=["a", missing, "c", "d", "e"], C=[1.1, 2.2, 3.3, 4.4, 5.5]);

julia> write_gsheet(df, full, sheet = "sheet2", append = false)
```
