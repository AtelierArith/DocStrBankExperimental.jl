```
defLoadVars(vars, df, dimsNameCols; <keyword arguments>)
```

Define the required IndexedTables or Arrays and load the data from a DataFrame in long format while specifing the dimensional columns and the column containing the variable names.

Like `varLoadVar` but here we are extracting multiple variables at once, with one column of the input dataframe storing the variable name.

# Arguments

  * `vars`: The array of variables to lookup
  * `df`: The source of the dataframe, that must be in the format dim1|dim2|...|varName|value
  * `dimsNameCols`: The name of the column containing the dimensions over which the variables are defined
  * `varNameCol (def: "varName")`: The name of the column in the df containing the variables names
  * `valueCol (def: "value")`: The name of the column in the df containing the values
  * `sparse (def: "true")`: Wheter to return `NDSparse` elements (from IndexedTable) or standard arrays
  * `missingValue` (def=`missing`): How to fill the matrix with (relevant only for arrays)
  * `fullKeys` (def=`true`): Wheter all the outputed variables should be based on the full set of keys,  or look for each of them on the keys found specifically for it in the filtered input dataframe

# Notes

  * Sparse indexed tables can be accessed by element but are slower, standard arrays need to be accessed by position but are faster
  * At the moment `sameKeys=true` is implemented only for the non-sparse case

# Examples

```julia
julia> (vol,numberOfTrees)  = defVars(["vol","numberOfTrees"], forestData,["region","treeSpecie","year"], varNameCol="parName", valueCol="value")
```
