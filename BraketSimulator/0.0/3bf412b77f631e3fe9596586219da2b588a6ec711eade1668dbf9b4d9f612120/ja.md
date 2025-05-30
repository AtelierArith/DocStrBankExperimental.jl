```
evolve!(dms::DensityMatrixSimulator{T, S<:AbstractMatrix{T}}, operations::Vector{Instruction}) -> DensityMatrixSimulator{T, S}
```

`dms`に含まれる密度行列に対して、`operations`の各操作をインプレースで適用します。

実質的に、各操作$\hat{A}$に対して次の操作を行います：

$$
\hat{\rho} \to \hat{A}^\dag \hat{\rho} \hat{A}
$$
