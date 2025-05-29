```
struct BeaTable
```

A BEA table with data and metadata returned from a [`bea_table`](@ref) call.

## Fields

  * `dataset`: dataset the table was retrieved from
  * `table_number`: the non-API table number
  * `table_description`: description of the data contained in the table
  * `metric`: measurement metric for the data, e.g. index, dollars, etc.
  * `units`: billions, millions, etc.
  * `line_descriptions`: `DataFrame` containing line number descriptions
  * `table_notes`: `DataFrame` containing any notes for the table
  * `frequency`: (M)onthly, (Q)uarterly, or (A)nnual
  * `data_startyear`: first year of data returned (may differ from what was requested)
  * `data_endyear`: last year of data returned (may differ from what was requested)
  * `api_tablename`: `TableName` parameter value for the table
  * `last_revised`: date the table was last revised
  * `data_values`: `DataFrame` containing the table data values
