```
mat2sparseform_nonstd(M, wt, [L], [ϵ])
```

行列 `M` をウェーブレット基底に変換します。次に、それは非標準形式に伸ばされます。 `ϵ * 最大列ノルム` を超える要素はゼロに設定されます。結果として得られる出力スパース行列は、`nonstd_wavemult` の入力として使用できます。

# 引数

  * `M::AbstractMatrix{T} where T<:AbstractFloat`: スパース非標準形式に変換される `n` by `n` 行列（`n` は二進数）。
  * `wt::OrthoFilter`: ウェーブレットフィルタ。
  * `L::Integer`: （デフォルト: `maxtransformlevels(M)`）分解レベルの数。
  * `ϵ::T where T<:AbstractFloat`: （デフォルト: `1e-4`）切断基準。

# 戻り値

  * `NM::SparseMatrixCSC{T, Integer}`: サイズ 2n x 2n の行列のスパース非標準形式。

# 例

```jldoctest
julia> using Wavelets, WaveletsExt; import Random: seed!

julia> seed!(1234); M = randn(4,4); wt = wavelet(WT.haar);

julia> mat2sparseform_nonstd(M, wt)
8×8 SparseArrays.SparseMatrixCSC{Float64, Int64} with 16 stored entries:
 1.88685   ⋅    ⋅         ⋅          ⋅         ⋅         ⋅          ⋅
  ⋅        ⋅    ⋅         ⋅          ⋅         ⋅         ⋅          ⋅
  ⋅        ⋅    ⋅        0.363656    ⋅         ⋅         ⋅          ⋅
  ⋅        ⋅   2.49634  -1.08139     ⋅         ⋅         ⋅          ⋅
  ⋅        ⋅    ⋅         ⋅          ⋅         ⋅       -1.0187     0.539411
  ⋅        ⋅    ⋅         ⋅          ⋅         ⋅        1.68141    0.0351839
  ⋅        ⋅    ⋅         ⋅        -1.39713  -1.21352   0.552745   0.427717
  ⋅        ⋅    ⋅         ⋅        -1.05882   0.16666  -0.124156  -0.218902
```

**参照:** [`mat2sparseform_std`](@ref), [`stretchmatrix`](@ref)
