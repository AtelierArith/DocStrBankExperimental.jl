```
BIC(m::UBCM)
```

UBCMモデル`m`のベイズ情報基準（BIC）を計算します。モデルのパラメータは事前に計算されている必要があります。BICはAICよりも制約が厳しいと考えられており、前者は後者が好むよりも少ないパラメータを持つモデルを好みます。

# 例

```julia-repl
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> solve_model!(model);

julia> BIC(model)
552.5770135138283

```

参照してください [`AIC`](@ref MaxEntropyGraphs.AIC), [`L_UBCM_reduced`](@ref MaxEntropyGraphs.L_UBCM_reduced).
