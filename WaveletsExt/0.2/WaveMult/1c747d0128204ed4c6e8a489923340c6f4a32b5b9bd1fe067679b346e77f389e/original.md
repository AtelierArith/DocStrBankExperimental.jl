```
mat2sparseform_nonstd(M, wt, [L], [ϵ])
```

Transform the matrix `M` into the wavelet basis. Then, it is stretched into its nonstandard form. Elements exceeding `ϵ * maximum column norm` are set to zero. The resulting output sparse matrix, and can be used as input to `nonstd_wavemult`.

# Arguments

  * `M::AbstractMatrix{T} where T<:AbstractFloat`: `n` by `n` matrix (`n` dyadic) to be put in Sparse Nonstandard form.
  * `wt::OrthoFilter`: Wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(M)`) Number of decomposition levels.
  * `ϵ::T where T<:AbstractFloat`: (Default: `1e-4`) Truncation Criterion.

# Returns

  * `NM::SparseMatrixCSC{T, Integer}`: Sparse nonstandard form of matrix of size 2n x 2n.

# Examples

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

**See also:** [`mat2sparseform_std`](@ref), [`stretchmatrix`](@ref)
