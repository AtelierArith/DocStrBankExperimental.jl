```
create_independent(x::Union{Cdouble, Vector{Cdouble}})
```

引数 `x` をテープ上の独立変数としてマークし、`x` のために微分可能な `Adouble{TbAlloc}` を作成します。
