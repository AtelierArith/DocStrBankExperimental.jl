```
compute_MM(nep::NEP,S,V)
```

Computes the sum $Σ_i M_i V f_i(S)$ for a NEP, where $S$ and $V$ are matrices, and the NEP satisfies $M(λ)=Σ_i M_i f_i(λ)$.

# Example

This example shows that for diagonal `S`, the result of `compute_MM` can also be computed with `compute_Mlincomb`

```julia-repl
julia> nep=nep_gallery("dep0");
julia> D=diagm(0 => [1,2])
2×2 Array{Int64,2}:
 1  0
 0  2
julia> V=ones(size(nep,1),2);
julia> W=compute_MM(nep,D,V);
julia> norm(W[:,1]-compute_Mlincomb(nep,D[1,1],V[:,1]))
0.0
julia> norm(W[:,2]-compute_Mlincomb(nep,D[2,2],V[:,2]))
4.440892098500626e-16
```

# Reference

Properties of the quantity $Σ_i M_i V f_i(S)$ for non-polynomial nonlinear eigenvalue problems were extensively used in:

  * D. Kressner A block Newton method for nonlinear eigenvalue problems, Numer. Math., 114 (2) (2009), pp. 355-372
  * C. Effenberger, Robust solution methods for nonlinear eigenvalue problems, PhD thesis, 2013, EPF Lausanne
