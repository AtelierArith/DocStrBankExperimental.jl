```
LRNData
```

`LRNData` represents the contents of a `*.lrn` file with the following fields:

  * `data::Matrix{Float64}`

    Matrix of data, cases in rows, variables in columns
  * `column_types::Array{LRNCType, 1}`

    Column types, see `LRNCType`
  * `key::Array{Integer, 1}`

    Unique key for each line
  * `names::Array{String, 1}`

    Column names
  * `key_name::String`

    Name for key column
  * `comment::String`

    Comments about the data
