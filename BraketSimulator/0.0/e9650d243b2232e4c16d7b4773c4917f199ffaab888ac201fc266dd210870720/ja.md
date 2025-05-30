```
evolve!(svs::StateVectorSimulator{T, S<:AbstractVector{T}}, operations::Vector{Instruction}) -> StateVectorSimulator{T, S}
```

`operations`の各操作を`svs`に含まれる状態ベクトルに対してインプレースで適用します。

実質的に、各操作$\hat{A}$に対して次の操作を行います：

$$
\left| \psi \right\rangle \to \hat{A} \left| \psi \right\rangle
$$
