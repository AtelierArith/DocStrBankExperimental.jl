```
function averagebymass(data, symbol::Symbol)
function averagebymass(data::StructArray, symbol::Symbol)
```

Average on field `symbol` weighted by `:Mass` of elements in an array of dict of arrays

## Examples

```jl
averagebymass(data, :Pos)
```
