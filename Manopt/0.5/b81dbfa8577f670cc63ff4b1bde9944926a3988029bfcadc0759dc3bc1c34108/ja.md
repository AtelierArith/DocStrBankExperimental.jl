```
get_gradient(M::AbstractManifold, sgo::ManifoldStochasticGradientObjective, p, k)
get_gradient!(M::AbstractManifold, sgo::ManifoldStochasticGradientObjective, Y, p, k)
```

$$
k∈\{1,…,n\}
$$

のいずれかの和の勾配$\operatorname{grad}f_k$を`x`（`Y`の代わりに）で評価します。

確率的勾配に対して、インプレースで動作する単一の関数を使用する場合、割り当てに必要な勾配の長さ（または要素数）を決定できないため、[`get_gradient`](@ref)は利用できません。
