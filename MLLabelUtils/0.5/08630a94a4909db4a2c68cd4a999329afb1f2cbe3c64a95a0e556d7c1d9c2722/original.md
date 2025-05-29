```
isneglabel(x, encoding) -> Bool
```

Checks if the given value `x` can be interpreted as the negative label given the `encoding`. This function takes potential classification rules into account.

```
julia> isneglabel(0.6, LabelEnc.ZeroOne(0.5))
false

julia> isneglabel(0.4, LabelEnc.ZeroOne(0.5))
true

julia> isneglabel(:b, LabelEnc.NativeLabels([:a,:b]))
true
```
