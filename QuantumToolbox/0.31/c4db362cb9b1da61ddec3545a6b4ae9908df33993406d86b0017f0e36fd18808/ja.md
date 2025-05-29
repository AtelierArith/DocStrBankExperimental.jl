```
liouvillian(H::AbstractQuantumObject, c_ops::Union{Nothing,AbstractVector,Tuple}=nothing, Id_cache=I(prod(H.dimensions)))
```

システムハミルトニアン $\hat{H}$ と一連の崩壊演算子 $\{\hat{C}_n\}_n$ に対する Liouvillian [`SuperOperator`](@ref) を構築します：

$$
\mathcal{L} [\cdot] = -i[\hat{H}, \cdot] + \sum_n \mathcal{D}(\hat{C}_n) [\cdot]
$$

ここで 

$$
\mathcal{D}(\hat{C}_n) [\cdot] = \hat{C}_n [\cdot] \hat{C}_n^\dagger - \frac{1}{2} \hat{C}_n^\dagger \hat{C}_n [\cdot] - \frac{1}{2} [\cdot] \hat{C}_n^\dagger \hat{C}_n
$$

オプションの引数 `Id_cache` は、事前に計算された単位行列を渡すために使用できます。これは、同じ関数が既知のヒルベルト空間の次元で複数回適用される場合に便利です。

さらに [`spre`](@ref)、[`spost`](@ref)、および [`lindblad_dissipator`](@ref) を参照してください。
