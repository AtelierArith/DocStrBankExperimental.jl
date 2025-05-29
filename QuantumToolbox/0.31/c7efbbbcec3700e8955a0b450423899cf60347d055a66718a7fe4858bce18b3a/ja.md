```
sprepost(A::AbstractQuantumObject, B::AbstractQuantumObject)
```

`A`と`B`が密度行列演算子の左側と右側で作用する[`SuperOperator`](@ref)形式を返します: $\mathcal{O} \left( \hat{A}, \hat{B} \right) \left[ \hat{\rho} \right] = \hat{A} \hat{\rho} \hat{B}$。

密度行列は[`OperatorKet`](@ref)形式でベクトル化されているため: $|\hat{\rho}\rangle\rangle$、この[`SuperOperator`](@ref)は常に行列$\hat{B}^T \otimes \hat{A}$です。すなわち

$$
\mathcal{O} \left(\hat{A}, \hat{B}\right) \left[ \hat{\rho} \right] = \hat{B}^T \otimes \hat{A} ~ |\hat{\rho}\rangle\rangle = \textrm{spre}(\hat{A}) * \textrm{spost}(\hat{B}) ~ |\hat{\rho}\rangle\rangle
$$

（詳細については、ドキュメントのセクション: [Superoperators and Vectorized Operators](@ref doc:Superoperators-and-Vectorized-Operators)を参照してください）

また[`spre`](@ref)と[`spost`](@ref)も参照してください。
