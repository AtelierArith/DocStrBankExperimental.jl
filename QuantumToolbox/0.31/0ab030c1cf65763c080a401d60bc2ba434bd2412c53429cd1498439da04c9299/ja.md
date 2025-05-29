```
spre(A::AbstractQuantumObject, Id_cache=I(size(A,1)))
```

は、密度行列演算子の左側で作用する `A` の [`SuperOperator`](@ref) 形式を返します: $\mathcal{O} \left(\hat{A}\right) \left[ \hat{\rho} \right] = \hat{A} \hat{\rho}$。

密度行列は [`OperatorKet`](@ref) 形式でベクトル化されているため: $|\hat{\rho}\rangle\rangle$、この [`SuperOperator`](@ref) は常に行列 $\hat{\mathbb{1}} \otimes \hat{A}$ です、すなわち 

$$
\mathcal{O} \left(\hat{A}\right) \left[ \hat{\rho} \right] = \hat{\mathbb{1}} \otimes \hat{A} ~ |\hat{\rho}\rangle\rangle
$$

（詳細については、ドキュメントのセクション: [Superoperators and Vectorized Operators](@ref doc:Superoperators-and-Vectorized-Operators) を参照してください）

オプションの引数 `Id_cache` は、事前に計算された単位行列を渡すために使用できます。これは、同じ関数が既知のヒルベルト空間次元で複数回適用される場合に便利です。

また、[`spost`](@ref) と [`sprepost`](@ref) も参照してください。
