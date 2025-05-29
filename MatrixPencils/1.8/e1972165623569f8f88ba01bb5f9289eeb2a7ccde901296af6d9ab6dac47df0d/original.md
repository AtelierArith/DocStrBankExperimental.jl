```
lsminreal(A, E, B, C, D; fast = true, atol1 = 0, atol2, rtol, contr = true, obs = true, noseig = true) 
          -> (Ar, Er, Br, Cr, Dr, nuc, nuo, nse)
```

Reduce the linearization `(A-λE,B,C,D)` of a rational matrix to a reduced form `(Ar-λEr,Br,Cr,Dr)` such that

```
         -1                    -1
 C*(λE-A)  *B + D = Cr*(λEr-Ar)  *Br + Dr
```

with the least possible order `nr` of `Ar-λEr` if `contr = true`, `obs = true` and `nseig = true`.  Such a realization is called `minimal` and satisfies:

```
 (1) rank[Br Ar-λEr] = nr for all finite λ (finite controllability)

 (2) rank[Br Er] = nr (infinite controllability)

 (3) rank[Ar-λEr; Cr] = nr for all finite λ (finite observability)

 (4) rank[Er; Cr] = nr (infinite observability)

 (5) Ar-λEr has no simple infinite eigenvalues
```

A realization satisfying only conditions (1)-(4) is called `irreducible`. 

The achieved dimensional reductions to fulfill conditions (1) and (2), conditions (3) and (4), and  respectively, condition (5) are returned in `nuc`, `nuo`, `nse`. 

Some reduction steps can be skipped by appropriately selecting the keyword arguments `contr`, `obs` and `nseig`. 

If `contr = false`, then the controllability conditions (1) and (2) are not enforced. 

If `obs = false`, then observability condition (3) and (4) are not enforced.

If `nseig = false`, then condition (5) on the lack of simple infinite eigenvalues is not enforced. 

To enforce conditions (1)-(4), orthogonal similarity transformations are performed on  the matrices of the original linearization `(A-λE,B,C,D)` to obtain an irreducible linearization using structured pencil reduction algorithms, as the fast versions of the reduction techniques of the  full row rank pencil [B A-λE] and full column rank pencil [A-λE;C] proposed in [1].  To enforce condition (5), residualization formulas (see, e.g., `[2, page 329]`) are employed which involves matrix inversions. 

The underlying pencil manipulation algorithms employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `A`, `B`, `C`, `D`, the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`. 

[1] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[2] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017. 
