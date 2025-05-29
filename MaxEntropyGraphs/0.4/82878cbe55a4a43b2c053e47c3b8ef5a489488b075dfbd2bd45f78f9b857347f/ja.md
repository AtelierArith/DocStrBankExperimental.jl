```
BIC(m::BiCM)
```

BiCMモデル`m`のベイズ情報基準（BIC）を計算します。モデルのパラメータは事前に計算されている必要があります。BICはAICよりも制約が厳しいと考えられており、前者は後者が好むよりも少ないパラメータを持つモデルを好みます。

# 例

```julia-repl
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

julia> BIC(model)
579.3789571131789

```

参照してください [`AIC`](@ref MaxEntropyGraphs.AIC), [`L_BiCM_reduced`](@ref MaxEntropyGraphs.L_BiCM_reduced).
