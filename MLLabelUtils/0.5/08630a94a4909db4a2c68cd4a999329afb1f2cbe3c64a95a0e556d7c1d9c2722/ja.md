```
isneglabel(x, encoding) -> Bool
```

与えられた値 `x` が `encoding` に基づいて負のラベルとして解釈できるかどうかをチェックします。この関数は潜在的な分類ルールを考慮に入れます。

```
julia> isneglabel(0.6, LabelEnc.ZeroOne(0.5))
false

julia> isneglabel(0.4, LabelEnc.ZeroOne(0.5))
true

julia> isneglabel(:b, LabelEnc.NativeLabels([:a,:b]))
true
```
