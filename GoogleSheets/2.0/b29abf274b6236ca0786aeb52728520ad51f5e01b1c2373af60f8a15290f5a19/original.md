```
freeze!(client::GoogleSheetsClient, sheet::Sheet, rows::Int64=0, cols::Int64=0)::Dict{Any,Any}
```

Freeze rows and columns in a sheet.

# Arguments

  * `client::GoogleSheetsClient`: client
  * `sheet::Sheet`: sheet
  * `rows::Int64=0`: number of rows
  * `cols::Int64=0`: number of columns
