```
mmread(filename, infoonly=false, retcoord=false)
```

Read the contents of the Matrix Market file `filename` into a matrix, which will be either sparse or dense, depending on the Matrix Market format indicated by `coordinate` (coordinate sparse storage), or `array` (dense array storage).

# Arguments

  * `filename::String`: The file to read.
  * `infoonly::Bool=false`: Only information on the size and structure is returned from   reading the header. The actual data for the matrix elements are not parsed.
  * `retcoord::Bool`: If it is `true`, the rows, column and value vectors are returned along   with the header information.
