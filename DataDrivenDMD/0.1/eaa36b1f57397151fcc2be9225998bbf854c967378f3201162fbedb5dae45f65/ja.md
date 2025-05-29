```julia
mutable struct FBDMD{R} <: DataDrivenDMD.AbstractKoopmanAlgorithm
```

前方-後方DMDを介してコープマン演算子`K`を近似します。`K = sqrt(K₁*inv(K₂))`と仮定されており、ここで`K₁`は前方による近似、`K₂`は[DMDSVD](@ref)によるものです。[この論文](https://arxiv.org/pdf/1507.02264.pdf)に基づいています。

`truncation` ∈ (0, 1) が与えられた場合、特異値分解は`truncation*maximum(Σ)`より大きいエントリのみを含むように削減されます。`truncation`が整数の場合、計算には`truncation`までの削減されたSVDが使用されます。

# フィールド

  * `alg`

# シグネチャ
