```
λ,v = polyeig([eltype],nep::ChebPEP)
```

Computes a companion linearization for the NEP represented in a Chebyshev basis, and returns eigenpairs.

# Example

```julia
julia> using LinearAlgebra
julia> nep=nep_gallery("dep0");
julia> chebpep=ChebPEP(nep,9,-3,1,cosine_formula_cutoff=5);
julia> (λv,V)=polyeig(chebpep);
julia> ii=argmin(abs.(λv));
julia> λ=λv[ii];
julia> v=V[:,ii];
julia> norm(compute_Mlincomb(chebpep,λ,v))
1.3543968603949142e-14
julia> # Actually, it's not a bad approx to the original NEP either
julia> norm(compute_Mlincomb(nep,λ,v))
4.326355966047557e-6
```

See also [`ChebPEP`](@ref).

# References:

  * Amiraslani, A., Corless, R. M. & Lancaster, P. "Linearization of matrix polynomials expressed in poly-nomial bases" IMA J. Numer. Anal.,29 (2009): 141–157.
  * Effenberger and Kressner. "Chebyshev interpolation for nonlinear eigenvalue problems." BIT Numerical Mathematics 52.4 (2012): 933-951.
