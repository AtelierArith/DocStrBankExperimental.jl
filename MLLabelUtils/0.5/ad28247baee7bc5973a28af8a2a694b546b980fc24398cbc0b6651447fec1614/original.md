```
islabelenc(obj, encoding) -> Bool
```

Checks is the given object `obj` can be described as being produced by the given `encoding` in which case the function returns true, or false otherwise.

```
julia> islabelenc([1,0,1], LabelEnc.ZeroOne)
true

julia> islabelenc([1,-1,1], LabelEnc.ZeroOne)
false
```
