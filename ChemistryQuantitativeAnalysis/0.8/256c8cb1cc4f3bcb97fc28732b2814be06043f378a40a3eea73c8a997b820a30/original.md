```
findanalyte(dt::AbstractDataTable{A}, analyte::B) where {A, B <: A}
findanalyte(dt::AbstractDataTable, analyte::Symbol)
```

Return the index of the first element of `analyteobj(dt)` or `analytename(dt)` for which the element equals to `analyte`.
