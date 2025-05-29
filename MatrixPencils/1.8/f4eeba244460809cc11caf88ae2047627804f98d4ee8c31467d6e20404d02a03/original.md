```
lsminreal(A, B, C; fast = true, atol = 0, rtol, contr = true, obs = true, noseig = true) 
          -> (Ar, Br, Cr, nuc, nuo)
```

Reduce the linearization `(A-λI,B,C,0)` of a strictly proper rational matrix to a reduced form `(Ar-λI,Br,Cr,0)` such that

```
         -1                 -1
 C*(λI-A)  *B  = Cr*(λI-Ar)  *Br
```

with the least possible order `nr` of `Ar` if `contr = true` and `obs = true`.  Such a realization is called `minimal` and satisfies:

```
 (1) rank[Br Ar-λI] = nr for all λ (controllability);

 (2) rank[Ar-λI; Cr] = nr for all λ (observability).
```

The achieved dimensional reductions to fulfill conditions (1) and (2) are returned in `nuc` and `nuo`, respectively. 

Some reduction steps can be skipped by appropriately selecting the keyword arguments `contr` and `obs`. 

If `contr = false`, then the controllability condition (1) is not enforced. 

If `obs = false`, then observability condition (2) is not enforced.

To enforce conditions (1)-(2), orthogonal similarity transformations are performed on  the matrices of the original linearization `(A-λI,B,C,0)` to obtain a minimal linearization using structured pencil reduction algorithms, as the fast versions of the reduction techniques of the  full row rank pencil [B A-λI] and full column rank pencil [A-λI;C] proposed in [1]. 

The underlying pencil manipulation algorithms employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

The keyword arguments `atol` and `rtol`, specify, respectively, the absolute and relative tolerances for the  nonzero elements of matrices `A`, `B`, `C`.  

[1] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.
