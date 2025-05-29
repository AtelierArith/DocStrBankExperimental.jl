```
ELEMENT(self::AbaqusExporter, TYPE::AbstractString, ELSET::AbstractString,
  start::Integer, conn::AbstractArray{T, 2}) where {T<:Integer}
```

Write out the `*ELEMENT` option.

`TYPE`= element type code, `ELSET`= element set to which the elements belong, `start`= start the element numbering at this integer, `conn`= connectivity array for the elements, one row per element
