```
batch_update!(client::GoogleSheetsClient, spreadsheet::Spreadsheet, body::Dict)::Dict{Any,Any}
```

Applies one or more updates to a spreadsheet.

Each request is validated before being applied. If any request is not valid then the entire request will fail and nothing will be applied.

Common batch_update! functionality: Charts: https://developers.google.com/sheets/api/reference/rest/v4/spreadsheets/charts Filters: https://developers.google.com/sheets/api/guides/filters Basic formatting: https://developers.google.com/sheets/api/samples/formatting Conditional formatting: https://developers.google.com/sheets/api/samples/conditional-formatting Conditional formatting: https://developers.google.com/sheets/api/guides/conditional-format

# Arguments

  * `client::GoogleSheetsClient`: client
  * `spreadsheet::Spreadsheet`: spreadsheet
  * `body::Dict`: updte body
