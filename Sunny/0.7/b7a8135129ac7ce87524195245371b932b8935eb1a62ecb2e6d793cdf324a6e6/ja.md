```
q_space_path(cryst::Crystal, qs, n; labels=nothing)
```

`n`個の波ベクトルからなる1Dパスを返します。これは`qs`の点の間を部分的に線形にサンプリングしたものです。`qs`は逆格子単位（RLU）で提供されますが、連続するサンプルはグローバル（逆長さ）デカルト座標系で均等に間隔を置かれています。オプションの`labels`は各特別なq点に関連付けることができ、プロット関数で使用されます。

[`q_space_grid`](@ref)も参照してください。
