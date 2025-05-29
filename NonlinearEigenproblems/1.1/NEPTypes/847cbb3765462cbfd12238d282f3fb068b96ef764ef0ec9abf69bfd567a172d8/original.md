```
ChebPEP(orgnep::NEP,k,[a=-1,[b=1]] [,cosine_formula_cutoff=5])
```

The type `ChebPEP<:AbstractSPMF` represents a polynomial function where the function is stored using a Chebyshev basis scaled to the interval `[a,b]`, i.e.,

$$
M(λ)= B_0T_0(λ)+⋯+B_{k-1}T_{k-1}(λ)
$$

where $T_i$ are the scaled and shifted Chebyshev polynomials.

The constructor `ChebPEP` takes `nep::NEP` as an input and interpolates this NEP in `k` Chebyshev nodes, resulting in a polynomial of degree `k-1`, represented by its coefficients in the Chebyshev basis. Interpolation in Chebyshev nodes and representation with Chebyshev basis, is known to have attractive approximation properties, as well as robustness with respect to round-off errors.

The kwarg `cosine_formula_cutoff` decides how the Chebyshev polynomials should be computed. For larger degrees, it is better to use the cosine formula, whereas for low degrees the explicit monomial expression is more efficient. The explicit monomial expression will be used for degrees lower than `cosine_formula_cutoff`.

# Example:

```julia
julia> nep=nep_gallery("dep0");
julia> chebpep=ChebPEP(nep,9);
julia> using LinearAlgebra;
julia> norm(compute_Mder(nep,0.3)-compute_Mder(chebpep,0.3))
1.2881862971045282e-8
julia> chebpep=ChebPEP(nep,19); # Better interpolation
julia> norm(compute_Mder(nep,0.3)-compute_Mder(chebpep,0.3))
2.0312004517316714e-15
```

See also: [`polyeig`](methods.md#NonlinearEigenproblems.NEPSolver.polyeig), [`PEP`](@ref)
