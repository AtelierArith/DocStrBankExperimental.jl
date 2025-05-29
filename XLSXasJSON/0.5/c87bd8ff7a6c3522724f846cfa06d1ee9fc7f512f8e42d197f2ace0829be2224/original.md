```
JSONWorksheet
```

construct 'Array{OrderedDict, 1}' for each row from Worksheet

# Constructors

```julia
JSONWorksheet("Example.xlsx", "Sheet1")
JSONWorksheet("Example.xlsx", 1)

```

# Arguments

  * `row_oriented` : if 'true'(the default) it will look for colum names in '1:1', if `false` it will look for colum names in 'A:A'
  * `start_line` : starting index of position of columnname.
  * `squeeze` : squeezes all rows of Worksheet to a singe row.
  * `delim` : a String or Regrex that of deliminator for converting single cell to array.
