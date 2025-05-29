```
NSET_NSET(self::AbaqusExporter, NSET::AbstractString,
  n::AbstractVector{T}) where {T<:Integer}
```

Write out the `*NSET` option.

`NSET` = name of the set, `n` = array of the node numbers
