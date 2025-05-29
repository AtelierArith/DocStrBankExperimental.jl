```
get_gradients(M::AbstractManifold, sgo::ManifoldStochasticGradientObjective, p)
get_gradients!(M::AbstractManifold, X, sgo::ManifoldStochasticGradientObjective, p)
```

すべての和の勾配 $\{\operatorname{grad}f_i\}_{i=1}^n$ を `p` で評価します（`X` の代わりに）。

確率的勾配に対して単一の関数を使用する場合、それがインプレースで動作する場合、[`get_gradient`](@ref) は利用できません。なぜなら、勾配の長さ（または要素の数）を決定できないからです。
