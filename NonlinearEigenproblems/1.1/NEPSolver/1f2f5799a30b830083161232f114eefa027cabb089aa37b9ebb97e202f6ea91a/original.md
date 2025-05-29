```
 mslp([eltype],nep::NEP;[errmeasure,][tol,][maxit,][λ,][logger,][eigsolvertype::Type])
```

Runs the method of successive linear problems. The  method requires the solution of a generalized eigenvalue problem in every iteration. The method used for the eigenvalue computation is specified in eigsolvertype. See [`augnewton`](@ref) for other parameters.

# Example

Create a rational NEP using a [`SPMF_NEP`](@ref).

```julia-repl
julia> eye=Matrix{Float64}(I,3,3);
julia> Av=[ones(3,3),eye,triu(ones(3,3))];
julia> fv=[S-> S, S -> S^2, S->inv(S-one(S)*10)];
julia> nep=SPMF_NEP(Av,fv);
julia> (λ,v)=mslp(nep);
julia> compute_Mlincomb(nep,λ,v)
3-element Array{Complex{Float64},1}:
 -1.38778e-17+1.65715e-18im
 -5.55112e-17+1.30633e-17im
 -4.16334e-17-1.54436e-17im
```

# References

  * A. Ruhe, Algorithms for the nonlinear eigenvalue problem, SIAM J. Numer. Anal. 10 (1973) 674-689
