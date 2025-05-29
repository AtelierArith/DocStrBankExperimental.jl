```
lindblad_dissipator(O::AbstractQuantumObject, Id_cache=I(size(O,1))
```

リンドブラッド [`SuperOperator`](@ref) を次のように定義します。

$$
\mathcal{D} \left( \hat{O} \right) \left[ \hat{\rho} \right] = \frac{1}{2} \left( 2 \hat{O} \hat{\rho} \hat{O}^\dagger - 
\hat{O}^\dagger \hat{O} \hat{\rho} - \hat{\rho} \hat{O}^\dagger \hat{O} \right)
$$

オプションの引数 `Id_cache` は、事前に計算された単位行列を渡すために使用できます。これは、同じ関数が既知のヒルベルト空間の次元で複数回適用される場合に便利です。

他にも [`spre`](@ref)、[`spost`](@ref)、および [`sprepost`](@ref) を参照してください。
