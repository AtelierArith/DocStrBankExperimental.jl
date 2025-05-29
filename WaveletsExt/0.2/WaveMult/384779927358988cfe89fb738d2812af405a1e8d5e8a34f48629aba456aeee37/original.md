```
nonstd_wavemult(M, x, wt, [L], [ϵ])
nonstd_wavemult(NM, x, wt, [L])
```

If `M` is an $n$ by $n$ matrix, there are two ways to compute $y = Mx$. The first is to use the standard matrix multiplication to compute the product. This algorithm works in order of $O(n^2)$, where $n$ is the length of `x`.

The second is to transform both the matrix and vector to their nonstandard forms and multiply the nonstandard forms. If the matrix is sparse in nonstandard form, this can be an order $O(n)$ algorithm.

!!! tip
    One may choose to use the original matrix `M` as input by doing `nonstd_wavemult(M, x, wt, [L], [ϵ])`. However, if the nonstandard form sparse matrix `NM` is already computed prior, one can skip the redundant step by doing `nonstd_wavemult(NM, x, wt, [L])`.


# Arguments

  * `M::AbstractVector{T} where T<:AbstractFloat`: $n$ by $n$ matrix.
  * `NM::SparseMatrixCSC{T,S} where {T<:AbstractFloat, S<:Integer}`: Nonstandard transformed sparse matrix of `M`.
  * `x::AbstractVector{T} where T<:AbstractFloat`: Vector of length $n$ in natural basis.
  * `wt::OrthoFilter`: Type of wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of decomposition levels.
  * `ϵ::T where T<:AbstractFloat`: (Default: `1e-4`) Truncation criterion for nonstandard transform of `M`.

# Returns

  * `y::Vector{T}`: Standard approximation of $Mx$.

# Examples

```jldoctest
julia> using Wavelets, WaveletsExt

julia> M = randn(4,4); x = randn(4); wt = wavelet(WT.haar);

julia> NM = mat2sparseform_nonstd(M, wt); y₀ = nonstd_wavemult(NM, x, wt)
4-element Vector{Float64}:
 -1.2590015844047044
 -1.3234024176418535
  2.1158027198405627
  1.5364835417087566

julia> y₁ = nonstd_wavemult(M, x, wt)
4-element Vector{Float64}:
 -1.2590015844047044
 -1.3234024176418535
  2.1158027198405627
  1.5364835417087566

julia> y₀ == y₁                     # Both methods are equivalent
true
```

**See also:* [`std_wavemult`](@ref), [`mat2sparseform_nonstd`](@ref), [`ns_dwt`](@ref), [`ns_idwt`](@ref) 
