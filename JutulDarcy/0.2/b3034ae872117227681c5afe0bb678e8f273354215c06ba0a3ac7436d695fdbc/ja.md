```
get_1d_reservoir(nc;
    L = 1.0,
    perm = 9.8692e-14, # 0.1 darcy
    poro = 0.1,
    area = 1.0,
    z_max = nothing
)
```

`nc` セルと長さ `L` を持つ 1D 貯留層ドメインを設定するためのユーティリティ関数です。一般的には [`reservoir_domain`](@ref) 関数が好まれ、この関数は後方互換性のために保持されています。
