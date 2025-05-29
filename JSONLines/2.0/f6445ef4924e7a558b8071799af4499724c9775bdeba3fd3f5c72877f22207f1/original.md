```
settypes!(lines::LineIndex, d::Union{Dict{Symbol, DataType}, Dict{Symbol, UnionAll}, Dict{Symbol, Union}})
```

Manually set types for columns. `d` is a `Dict` in which keys are `Symbol`s corresponding to columnnames and values are the datatypes.
