```
r = gnrank(sys, fastrank = true, atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ )
```

Compute the normal rank `r` of the transfer function matrix `G(λ)` of the descriptor system `sys = (A-λE,B,C,D)`. 

The normal rank of `G(λ)` is evaluated as `r = k - n`, where `k` is the normal rank of the system matrix pencil 

```
          | A-λE | B | 
  S(λ) := |------|---|
          |  C   | D |
```

and `n` is the order of the system `sys` (i.e., the size of `A`). 

If `fastrank = true`, the normal rank of `S(λ)` is evaluated by counting the singular values of `S(γ)` greater than `max(max(atol1,atol2), rtol*σ₁)`,  where `σ₁` is the largest singular value of `S(γ)` and `γ` is a randomly generated value.  If `fastrank = false`, the rank is evaluated as `nr + ni + nf + nl`, where `nr` and `nl` are the sums of right and left Kronecker indices,  respectively, while `ni` and `nf` are the number of infinite and finite eigenvalues, respectively. The sums `nr+ni` and   `nf+nl` are determined from an appropriate Kronecker-like form of the pencil `S(λ)`, exhibiting the spliting of the right and left structures.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`,   the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
