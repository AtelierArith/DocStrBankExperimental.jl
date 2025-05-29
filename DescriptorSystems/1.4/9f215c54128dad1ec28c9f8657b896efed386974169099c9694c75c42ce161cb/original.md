```
isproper(sys; atol = 0, atol1 = atol, atol2 = atol, rtol = = n*ϵ, fast = true)
```

Return `true` if the transfer function matrix `G(λ)` of the descriptor system `sys = (A-λE,B,C,D)` is proper and `false` otherwise.  

For a descriptor system realization `sys = (A-λE,B,C,D)` without uncontrollable and unobservable infinite eigenvalues, it is checked that the pencil `A-λE` has no infinite eigenvalues or, if infinite eigenvalues exist, all infinite eigenvalues are simple. If the original descriptor realization has uncontrollable or unobservable infinite eigenvalues, these are elliminated using orthogonal pencil reduction algorithms. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`,   the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `n` is the order of `A` and `ϵ` is the working machine epsilon.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
