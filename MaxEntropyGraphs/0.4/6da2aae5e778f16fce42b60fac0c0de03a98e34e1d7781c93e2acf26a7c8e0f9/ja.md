```
L_BiCM_reduced(m::BiCM)
```

BiCMモデル`m`の対数尤度を、計算された最尤パラメータに基づいて返します。

# 例

```jldoctest
# DBCMモデルで使用する:
julia> G = corporateclub();

julia> model = BiCM(G);

julia> solve_model!(model);

julia> L_BiCM_reduced(model);

```

さらに[`L_BiCM_reduced(::Vector, ::Vector, ::Vector, ::Vector, ::Vector, ::UnitRange, ::UnitRange, ::Int)`](@ref)を参照してください。
