```
update!(client::GoogleSheetsClient, range::CellRange, df::DataFrame; kwargs...)::UpdateSummary
```

Updates a range of cell values in a spreadsheet.

# Arguments

  * `client::GoogleSheetsClient`: client for interacting with Google Sheets.
  * `range::CellRange`: cell range to modify.
  * `df::DataFrame`: dataframe of values.
  * `kwargs...`: keyword arguments.
