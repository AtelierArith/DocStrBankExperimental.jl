```julia
mutable struct TOTALDMD{R, A} <: DataDrivenDMD.AbstractKoopmanAlgorithm
```

コープマン演算子 `K` を、ランク削減されたデータ行列 `Xᵣ = X Qᵣ` と `Yᵣ = Y Qᵣ` に対してアルゴリズム `alg` を用いて近似します。ここで、`Qᵣ` は結合データ `Z = [X; Y]` の特異値分解から得られます。[この論文](http://cwrowley.princeton.edu/papers/Hemati-2017a.pdf)に基づいています。

もし `rtol` ∈ (0, 1) が与えられた場合、特異値分解は `rtol*maximum(Σ)` より大きいエントリのみを含むように削減されます。`rtol` が整数の場合、計算には `rtol` までの削減された SVD が使用されます。

# フィールド

  * `truncation`
  * `alg`

# シグネチャ
