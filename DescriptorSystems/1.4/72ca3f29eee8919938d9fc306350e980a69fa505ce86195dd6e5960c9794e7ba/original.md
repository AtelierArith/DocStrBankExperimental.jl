```
sysr = gir(sys; finite = true, infinite = true, contr = true, obs = true, noseig = false,
           fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol = nϵ)
```

Compute for a descriptor system `sys = (A-λE,B,C,D)` of order `n` a reduced order descriptor system   `sysr = (Ar-λEr,Br,Cr,Dr)` of order `nr ≤ n` such that `sys` and `sysr` have the same transfer function matrix, i.e., 

```
         -1                    -1
 C*(λE-A)  *B + D = Cr*(λEr-Ar)  *Br + Dr .
```

The least possible order `nr` is achieved if `finite = true`, `infinite = true`, `contr = true`,  `obs = true` and `nseig = true`. Such a realization is called `minimal` and satisfies:

```
 (1) rank[Br Ar-λEr] = nr for all finite λ (finite controllability)

 (2) rank[Br Er] = nr (infinite controllability)

 (3) rank[Ar-λEr; Cr] = nr for all finite λ (finite observability)

 (4) rank[Er; Cr] = nr (infinite observability)

 (5) Ar-λEr has no simple infinite eigenvalues
```

A realization satisfying only conditions (1)-(4) is called `irreducible` and is computed by default. 

Some reduction steps can be skipped by appropriately selecting the keyword arguments `contr`, `obs`, `finite`, `infinite` and `nseig`. 

If `contr = false`, then the controllability conditions (1) and (2) are not enforced.  If `contr = true` and `finite = true`, then the finite controllability condition (1) is enforced.  If `contr = true` and `finite = false`, then the finite controllability condition (1) is not enforced.  If `contr = true` and `infinite = true`, then the infinite controllability condition (2) is enforced.  If `contr = true` and `infinite = false`, then the infinite controllability condition (2) is not enforced. 

If `obs = false`, then observability condition (3) and (4) are not enforced. If `obs = true` and `finite = true`, then the finite observability condition (3) is enforced. If `obs = true` and `finite = false`, then the finite observability condition (3) is not enforced. If `obs = true` and `infinite = true`, then the infinite observability condition (4) is enforced. If `obs = true` and `infinite = false`, then the infinite observability condition (4) is not enforced.

If `nseig = true`, then condition (5) on the lack of simple infinite eigenvalues is also enforced. 

To enforce conditions (1)-(4), the `Procedure GIR` in `[1, page 328]` is employed, which performs  orthogonal similarity transformations on the matrices of the original realization `(A-λE,B,C,D)`  to obtain an irreducible realization using structured pencil reduction algorithms.  To enforce condition (5), residualization formulas (see, e.g., `[1, page 329]`) are employed which involves matrix inversions. 

The underlying pencil manipulation algorithms employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `A`, `B`, `C`, `D`, the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.  The default relative tolerance is `nϵ`, where `ϵ` is the working *machine epsilon*  and `n` is the order of the system `sys`.   The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 

[1] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017. 
