```
format_conditional!(client::GoogleSheetsClient, range::CellIndexRange2D, format::CellFormat, 
    condition_type::ConditionType, values...)::Dict{Any,Any}
```

Formats a range of cells if a condition is met.

# Arguments

  * `client::GoogleSheetsClient`: client.
  * `range::CellIndexRange2D`: cell index range.
  * `format::CellFormat`: cell format.
  * `condition_type::ConditionType`: type of condition.
  * `values...`: values for the condition.
