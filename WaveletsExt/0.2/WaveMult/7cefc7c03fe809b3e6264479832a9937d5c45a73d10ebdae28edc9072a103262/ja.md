```
mat2sparseform_std(M, wt, [L], [ϵ])
```

行列 `M` を標準形式に変換します。次に、`ϵ * 最大列ノルム` を超える要素はゼロに設定されます。結果として得られる出力スパース行列は、`std_wavemult` の入力として使用できます。

# 引数

  * `M::AbstractMatrix{T} where T<:AbstractFloat`: スパース標準形式に変換する行列。
  * `wt::OrthoFilter`: ウェーブレットフィルター。
  * `L::Integer`: (デフォルト: `maxtransformlevels(M)`) 分解レベルの数。
  * `ϵ::T where T<:AbstractFloat`: (デフォルト: `1e-4`) 切り捨て基準。

# 戻り値

  * `SM::SparseMatrixCSC{T, Integer}`: サイズ $n \times n$ の行列のスパース標準形式。

# 例

```jldoctest
julia> using Wavelets, WaveletsExt; import Random: seed!

julia> seed!(1234); M = randn(4,4); wt = wavelet(WT.haar);

julia> mat2sparseform_std(M, wt)
4×4 SparseArrays.SparseMatrixCSC{Float64, Int64} with 16 stored entries:
  1.88685    0.363656   0.468602   0.4063
  2.49634   -1.08139    1.90927   -0.356542
 -1.84601    0.129829   0.552745   0.427717
 -0.630852   0.866545  -0.124156  -0.218902
```

**参照:** [`mat2sparseform_nonstd`](@ref), [`sft`](@ref)
