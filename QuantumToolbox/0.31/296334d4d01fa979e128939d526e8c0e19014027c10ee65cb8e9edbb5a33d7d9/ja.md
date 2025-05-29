```
spost(B::AbstractQuantumObject, Id_cache=I(size(B,1)))
```

`B`の右側で密度行列演算子に作用する[`SuperOperator`](@ref)形式を返します: $\mathcal{O} \left(\hat{B}\right) \left[ \hat{\rho} \right] = \hat{\rho} \hat{B}$。

密度行列は[`OperatorKet`](@ref)形式でベクトル化されているため: $|\hat{\rho}\rangle\rangle$、この[`SuperOperator`](@ref)は常に行列$\hat{B}^T \otimes \hat{\mathbb{1}}$です。すなわち

$$
\mathcal{O} \left(\hat{B}\right) \left[ \hat{\rho} \right] = \hat{B}^T \otimes \hat{\mathbb{1}} ~ |\hat{\rho}\rangle\rangle
$$

（詳細については、ドキュメントのセクション: [Superoperators and Vectorized Operators](@ref doc:Superoperators-and-Vectorized-Operators)を参照してください）

オプションの引数`Id_cache`は、事前に計算された単位行列を渡すために使用できます。これは、同じ関数が既知のヒルベルト空間次元で複数回適用される場合に便利です。

[`spre`](@ref)および[`sprepost`](@ref)も参照してください。
