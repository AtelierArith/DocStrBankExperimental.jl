```
StopWhenGradientChangeLess <: StoppingCriterion
```

勾配の変化に基づく停止基準

```
\lVert \mathcal T_{p^{(k)}\gets p^{(k-1)} \operatorname{grad} f(p^{(k-1)}) -  \operatorname{grad} f(p^{(k-1)}) \rVert < ε
```

# コンストラクタ

```
StopWhenGradientChangeLess(
    M::AbstractManifold,
    ε::Float64;
    storage::StoreStateAction=StoreStateAction([:Iterate]),
    vector_transport_method::IRT=default_vector_transport_method(M),
)
```

勾配の変化に対する閾値 `ε` を持つ停止基準を作成します。つまり、この基準は [`get_gradient`](@ref) の変化のノルムが `ε` より小さいときに停止することを示します。ここで、`vector_transport_method` は使用されるベクトル輸送 $\mathcal T$ を示します。
