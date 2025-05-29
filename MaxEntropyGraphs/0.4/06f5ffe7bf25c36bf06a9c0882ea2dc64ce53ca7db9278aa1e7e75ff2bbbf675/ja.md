```
L_DBCM_reduced(m::DBCM)
```

DBCMモデル`m`の対数尤度を、計算された最尤パラメータに基づいて返します。

# 例

```jldoctest
# DBCMモデルで使用:
julia> G = MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques());

julia> model = DBCM(G);

julia> solve_model!(model);

julia> L_DBCM_reduced(model);

```

さらに[`L_DBCM_reduced(::Vector, ::Vector, ::Vector, ::Vector, ::Vector, ::Vector)`](@ref)を参照してください。
