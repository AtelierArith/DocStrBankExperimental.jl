```
get_gradient(M::AbstractManifold, sgo::ManifoldStochasticGradientObjective, p)
get_gradient!(M::AbstractManifold, sgo::ManifoldStochasticGradientObjective, X, p)
```

完全な勾配 $\operatorname{grad} f = \displaystyle\sum_{i=1}^n \operatorname{grad} f_i(p)$ を `p` で評価します（`X` の代わりに）。

確率的勾配のためにインプレースで動作する単一の関数を使用する場合、割り当てに必要な勾配の長さ（または要素数）を決定できないため、[`get_gradient`](@ref) は利用できません。
