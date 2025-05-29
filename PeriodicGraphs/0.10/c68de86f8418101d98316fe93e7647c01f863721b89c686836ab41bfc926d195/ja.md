```
normalize_cycle!(cycle::Vector{Int}, n, v::Val{D}) where D
```

`cycle`をインプレースで回転させ、場合によっては反転させます。`cycle`は`g`の頂点の`hash_position`である`Vector{Int}`であり、結果は同じサイクルを表すすべてのベクトルに対して同じになるようにします。これは、異なる単位セルに移動されたり回転されたりする可能性があります。

グラフ`g::PeriodicGraph{D}`は`n = nv(g)`および`v = Val(D)`として表されます。
