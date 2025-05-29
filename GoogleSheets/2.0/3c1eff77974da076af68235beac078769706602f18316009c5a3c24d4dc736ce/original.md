```
update!(client::GoogleSheetsClient, range::CellRange, values::Array{<:Any,2}; raw::Bool=false)::UpdateSummary
```

Updates a range of cell values in a spreadsheet.

# Arguments

  * `client::GoogleSheetsClient`: client for interacting with Google Sheets.
  * `range::CellRange`: cell range to modify.
  * `values::Array{<:Any,2}`: values to place in the spreadsheet.
  * `raw::Bool=false`: true treats values as raw, unparsed values and and are simply   inserted as a string.  false treats values exactly as if they were entered into   the Google Sheets UI, for example "=A1+B1" is a formula.
