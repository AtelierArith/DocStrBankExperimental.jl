```
 lsequal(A1, E1, B1, C1, D1, A2, E2, B2, C2, D2; 
         fastrank = true, atol1 = 0, atol2 = 0, rtol = min(atol1,atol2)>0 ? 0 : n*ϵ) -> flag::Bool
```

Check if two descriptor system linearizations `(A1-λE1,B1,C1,D1)` and `(A2-λE2,B2,C2,D2)` satisfy the equivalence condition  

```
            -1                      -1
 C1*(λE1-A1)  *B1 + D1 = C2*(λE2-A2)  *B2 + D2
```

The ckeck is performed by computing the normal rank `n` of the structured matrix pencil `M - λN`

```
          | A1-λE1   0    |   B1  | 
          |   0    A2-λE2 |   B2  | 
 M - λN = |---------------|-------|
          |   C1     -C2  | D1-D2 |
```

and verifying that `n = n1+n2`, where `n1` and `n2` are the orders of the square matrices `A1` and `A2`, respectively.

If `fastrank = true`, the rank is evaluated by counting how many singular values of `M - γ N` have magnitude  greater than `max(max(atol1,atol2), rtol*σ₁)`, where `σ₁` is the largest singular value of `M - γ N` and  `γ` is a randomly generated value [1].  If `fastrank = false`, the rank is evaluated as `nr + ni + nf + nl`, where `nr` and `nl` are the sums  of right and left Kronecker indices, respectively, while `ni` and `nf` are the number of infinite and  finite eigenvalues, respectively. The sums `nr+ni` and  `nf+nl`, are determined from an  appropriate Kronecker-like form (KLF) exhibiting the spliting of the right and left structures  of the pencil `M - λN`. For efficiency purpose, the reduction to the relevant KLF is only partially performed  using rank decisions based on rank revealing SVD-decompositions. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `M`, the absolute tolerance for the nonzero elements of `N` and the relative tolerance  for the nonzero elements of `M` and `N`. The default relative tolerance is `k*ϵ`, where `k` is the size of  the smallest dimension of `M`, and `ϵ` is the machine epsilon of the element type of `M`. 

[1] A. Varga, On checking null rank conditions of rational matrices, [arXiv:1812.11396](https://arxiv.org/abs/1812.11396), 2018.
