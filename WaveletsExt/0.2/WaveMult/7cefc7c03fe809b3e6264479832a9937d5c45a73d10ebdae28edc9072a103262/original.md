```
mat2sparseform_std(M, wt, [L], [ϵ])
```

Transform the matrix `M` into the standard form. Then, elements exceeding `ϵ * maximum column norm` are set to zero. The resulting output sparse matrix, and can be used as input to `std_wavemult`.

# Arguments

  * `M::AbstractMatrix{T} where T<:AbstractFloat`: Matrix to be put in Sparse Standard form.
  * `wt::OrthoFilter`: Wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(M)`) Number of decomposition levels.
  * `ϵ::T where T<:AbstractFloat`: (Default: `1e-4`) Truncation Criterion.

# Returns

  * `SM::SparseMatrixCSC{T, Integer}`: Sparse standard form of matrix of size $n 	imes n$.

# Examples

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

**See also:** [`mat2sparseform_nonstd`](@ref), [`sft`](@ref)
