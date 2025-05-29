```
delete_sheet!(client::GoogleSheetsClient, spreadsheet::Spreadsheet, title::AbstractString)::Dict{Any,Any}
```

Removes a sheet from a spreadsheet.

# Arguments

  * `client::GoogleSheetsClient`: client
  * `spreadsheet::Spreadsheet`: spreadsheet
  * `title::AbstractString`: sheet title
