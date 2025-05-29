```
E,A = companion(nep::PEP);
```

Linearizes a  polynomial eigenvalue problem (PEP) a to the companion form, as in the paper by Mehrmann and Voss. More precisely, for a k-th degree PEP with n-by-n coefficient matrices, this returns matrices E and A, both kn-by-kn, corresponding to the linearized problem

$$
Ax = λEx
$$

# Example

```julia-repl
julia> pep = nep_gallery("pep0");
julia> E,A = companion(pep);
julia> λ, V = eigen(A,E);
julia> minimum(svd(compute_Mder(pep,λ[1])).S)
2.4845217786736996e-12
```

# References

  * V. Mehrmann and H. Voss, Non-linear eigenvalue problems, a challenge for modern eigenvalue methods, GAMM‐Mitteilungen (2004)
