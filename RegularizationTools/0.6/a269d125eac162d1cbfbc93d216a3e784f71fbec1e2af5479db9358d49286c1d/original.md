```
Γ(m::Int, order::Int)
```

Return the smoothing matrix L for Tikhonov regularization of a system of size `m`.  Order can be 0, 1, ..., n. Code to generate matrix is based on the suggestion posted in Issue #7, which was inspired by Eilers, P. H. C. (2003). Analytical Chemistry, 75(14), 3631–3636. (Supporting Information).

```julia
L = Γ(m, 1)
```
