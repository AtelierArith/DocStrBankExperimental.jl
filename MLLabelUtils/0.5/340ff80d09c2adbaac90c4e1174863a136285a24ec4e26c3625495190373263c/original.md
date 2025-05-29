```
isposlabel(x, encoding) -> Bool
```

Checks if the given value `x` can be interpreted as the positive label given the `encoding`. This function takes potential classification rules into account.

```
julia> isposlabel(0.6, LabelEnc.ZeroOne(0.5))
true

julia> isposlabel(0.4, LabelEnc.ZeroOne(0.5))
false

julia> isposlabel(:b, LabelEnc.NativeLabels([:a,:b]))
false
```
