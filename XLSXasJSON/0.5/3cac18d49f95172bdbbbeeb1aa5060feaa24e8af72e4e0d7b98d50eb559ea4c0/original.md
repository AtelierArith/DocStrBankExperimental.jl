```
JSONWorkbook(file::AbstractString; start_line = 1)
```

`start_line` of each sheets are considered as JSONPointer for data structure.  And each sheets are pared to `Array{PointerDict, 1}` 

# Constructors

```julia
JSONWorkbook("Example.xlsx")
```

# Arguments

arguments are applied to all Worksheets within Workbook.

  * `row_oriented` : if 'true'(the default) it will look for colum names in '1:1', if `false` it will look for colum names in 'A:A'
  * `start_line` : starting index of position of columnname.
  * `squeeze` : squeezes all rows of Worksheet to a singe row.
  * `delim` : a String or Regrex that of deliminator for converting single cell to array.
