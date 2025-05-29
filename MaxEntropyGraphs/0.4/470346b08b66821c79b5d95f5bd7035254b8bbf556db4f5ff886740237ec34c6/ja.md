```
L_UBCM_reduced(m::UBCM)
```

UBCMモデル`m`の計算された最尤パラメータに基づく対数尤度を返します。

# 例

```jldoctest
# UBCMモデルで使用:
julia> G = MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate);

julia> model = UBCM(G);

julia> solve_model!(model);

julia> L_UBCM_reduced(model)
-168.68325136302832
```

詳細は[`L_UBCM_reduced(::Vector, ::Vector, ::Vector)`](@ref)を参照してください。
