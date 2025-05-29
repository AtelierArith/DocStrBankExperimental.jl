```
get_gradients(M::AbstractManifold, sgo::ManifoldStochasticGradientObjective, p)
get_gradients!(M::AbstractManifold, X, sgo::ManifoldStochasticGradientObjective, p)
```

すべての和の勾配 $\{\operatorname{grad}f_i\}_{i=1}^n$ を `p` で評価します（`X` の代わりに）。

確率的勾配のために単一の関数を使用する場合、それがインプレースで動作するなら、勾配の長さ（または要素数）を決定できないため、`get_gradient` は利用できません。
