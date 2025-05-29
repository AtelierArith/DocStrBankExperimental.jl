```
std_wavemult(M, x, wt, [L], [ϵ])
std_wavemult(SM, x, wt, [L])
```

If `M` is an $n$ by $n$ matrix, there are two ways to compute $y = Mx$. The first is to use the standard matrix multiplication to compute the product. This algorithm works in order of $O(n^2)$, where $n$ is the length of `x`.

The second is to transform both the matrix and vector to their standard forms and multiply the standard forms. If the matrix is sparse in standard form, this can be an order $O(n)$ algorithm.

!!! tip
    One may choose to use the original matrix `M` as input by doing `std_wavemult(M, x, wt, [L], [ϵ])`. However, if the standard form sparse matrix `SM` is already computed prior, one can skip the redundant step by doing `std_wavemult(SM, x, wt, [L])`.


# Arguments

  * `M::AbstractVector{T} where T<:AbstractFloat`: $n$ by $n$ matrix.
  * `NM::SparseMatrixCSC{T,S} where {T<:AbstractFloat, S<:Integer}`: Standard transformed sparse matrix of `M`.
  * `x::AbstractVector{T} where T<:AbstractFloat`: Vector of length $n$ in natural basis.
  * `wt::OrthoFilter`: Type of wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of decomposition levels.
  * `ϵ::T where T<:AbstractFloat`: (Default: `1e-4`) Truncation criterion for standard transform of `M`.

# Returns

  * `y::Vector{T}`: Standard form approximation of $Mx$.

# Examples

```jldoctest
julia> using Wavelets, WaveletsExt

julia> M = randn(4,4); x = randn(4); wt = wavelet(WT.haar);

julia> SM = mat2sparseform_std(M, wt); y₀ = std_wavemult(SM, x, wt)
4-element Vector{Float64}:
  2.2303830532617344
 -0.12704611958926648
  2.656411941014368
 -4.811388406857621

julia> y₁ = std_wavemult(M, x, wt)
4-element Vector{Float64}:
  2.2303830532617344
 -0.12704611958926648
  2.656411941014368
 -4.811388406857621

julia> y₀ == y₁
true
```

**See also:** [`nonstd_wavemult`](@ref), [`mat2sparseform_std`](@ref)
