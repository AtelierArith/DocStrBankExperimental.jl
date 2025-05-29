```
BIC(m::DBCM)
```

DBCMモデル`m`のベイズ情報基準（BIC）を計算します。モデルのパラメータは事前に計算されている必要があります。BICはAICよりも制約が厳しいと考えられており、前者は後者が好むよりも少ないパラメータを持つモデルを好みます。

# 例

```jldoctest
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> solve_model!(model);

julia> BIC(model)
415.69929372350714

```

参照してください [`AIC`](@ref MaxEntropyGraphs.AIC), [`L_DBCM_reduced`](@ref MaxEntropyGraphs.L_DBCM_reduced).
