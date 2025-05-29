```
defLoadVar(df, dimsNameCols; <keyword arguments>)
```

Define the required IndexedTables or Arrays and load the data from a DataFrame in long format while specifing the dimensional columns.

# Arguments

  * `df`: The source of the dataframe, that must be in the format dim1|dim2|...|value
  * `dimsNameCols`: The names of the columns corresponding to the dimensions over which the variables are defined (the keys)
  * `valueCol (def: "value")`: The name of the column in the df containing the values
  * `sparse (def: "true")`: Wheter to return `NDSparse` elements (from IndexedTable) or standard arrays
  * `missingValue` (def=`missing`): How to fill the matrix with (relevant only for arrays)

# Notes

  * Sparse indexed tables can be accessed by element but are slower, standard arrays need to be accessed by position but are faster

# Examples

```julia
julia> vol  = defVars(volumeData,["region","treeSpecie","year"], valueCol="value")
```
