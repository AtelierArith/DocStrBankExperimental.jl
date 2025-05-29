```
function Network(d::Dict; directed::Union{Bool,Missing}=missing)
```

辞書から `Network` を構築します。この辞書には少なくとも以下のキーが必要です：

1. `:Conductor`、[Conductor](@ref) 仕様を持つ辞書のベクター
2. `:Network`、少なくとも `:substation_bus` を持つ辞書

`directed` が欠けている場合、グラフはバスとエッジの数が放射状グラフを示唆する場合にのみ有向になります。
