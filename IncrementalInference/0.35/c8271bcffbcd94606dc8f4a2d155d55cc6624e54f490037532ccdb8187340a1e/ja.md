```julia
incrSuffix(lbl; ...)
incrSuffix(lbl, val; pattern)

```

DFG変数ラベルのサフィックス番号を増加または減少させるためのユーティリティ、例えば

```julia
incrSuffix(:x45_4)
# returns :x45_5

incrSuffix(:x45, +3)
# returns :x48

incrSuffix(:x45_4, -1)
# returns :x45_3
```

ノート

  * 別の動作のために `pattern::Regex=r"\d+"` を変更してください。
