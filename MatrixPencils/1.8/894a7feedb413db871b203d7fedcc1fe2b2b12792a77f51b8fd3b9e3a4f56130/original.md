```
lpsminreal(A, E, B, F, C, G, D, H; fast = true, atol1 = 0, atol2, rtol, contr = true, obs = true)  
           -> (Ar, Er, Br, Fr, Cr, Gr, Dr, Hr, V, W, nuc, nuo)
```

Reduce the linearization `(A-λE,B-λF,C-λG,D-λH)` of a rational matrix to a reduced form  `(Ar-λEr,Br-λFr,Cr-λGr,Dr-λHr)` such that, for appropriate  invertible upper triangular matrices `V` and `W`, 

```
                  -1                                     -1
 V'*((C-λG)*(λE-A)  *(B-λF) + D-λH)*W = (Cr-λGr)*(λEr-Ar)  *(Br-λFr) + Dr-λHr
```

with the least possible order `nr` of `Ar-λEr` if `contr = true` and `obs = true`. Such a realization is called `strongly minimal` and satisfies:

```
 (1) rank[Br-λFr Ar-λEr] = nr for all finite and infinite λ (strong controllability)

 (2) rank[Ar-λEr; Cr-λGr] = nr for all finite and infinite λ (strong observability)
```

The achieved dimensional reductions to fulfill conditions (1) and (2) are  returned in `nuc` and `nuo`, respectively. 

If `contr = true`, then the strong controllability condition (1) is enforced and `W` is an invertible upper triangular matrix or  `W = I` if `nuc = 0`. If `contr = false`, then the strong controllability condition (1) is not enforced and `W = I`. 

If `obs = true`, then the strong observability condition (2) is enforced and `V` is an invertible upper triangular matrix or  `V = I` if `nuo = 0`.  If `obs = false`, then the strong observability condition (2) is not enforced and `V = I`.

To enforce conditions (1) and (2), orthogonal similarity transformations are performed on  the matrices of the original linearization `(A-λE,B-λF,C-λG,D-λH)` to obtain a strongly minimal linearization  using structured pencil reduction algorithms [1]. The resulting realization `(Ar-λEr,Br-λFr,Cr-λGr,Dr-λHr)` fulfills the strong controllability and strong observability conditions established in [2]. 

The underlying pencil manipulation algorithms employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition, if `fast = false`. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `A`, `B`, `C`, `D`, the absolute tolerance for the nonzero elements of `E`, `F`, `G`, `H`   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`, `F`, `G`, `H`. 

[1] F.M. Dopico, M.C. Quintana and P. Van Dooren, Linear system matrices of rational transfer functions,  to appear in "Realization and Model Reduction of Dynamical Systems", A Festschrift to honor the 70th birthday of Thanos Antoulas",  Springer-Verlag. [arXiv:1903.05016](https://arxiv.org/pdf/1903.05016.pdf)

[2] G. Verghese, Comments on ‘Properties of the system matrix of a generalized state-space system’, Int. J. Control, Vol.31(5) (1980) 1007–1009.
