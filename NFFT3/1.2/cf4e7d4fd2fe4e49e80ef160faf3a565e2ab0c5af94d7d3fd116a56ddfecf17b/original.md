```
nfst_get_LinearMap(N::Vector{Int}, X::Array{Float64}; n, m::Integer, f1::UInt32, f2::UInt32)::LinearMap
```

gives an linear map which computes the NFST.

# Input

  * `N` - the multibandlimit $(N_1, N_2, \ldots, N_D)$ of the trigonometric polynomial $f$.
  * `X` - the nodes X.
  * `n` - the oversampling $(n_1, n_2, \ldots, n_D)$ per dimension.
  * `m` - the window size. A larger m results in more accuracy but also a higher computational cost.
  * `f1` - the NFST flags.
  * `f2` - the FFTW flags.

# See also

[`NFST{D}`](@ref)
