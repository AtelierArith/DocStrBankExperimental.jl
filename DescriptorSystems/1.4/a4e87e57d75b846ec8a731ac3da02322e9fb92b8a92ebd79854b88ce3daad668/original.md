```
isregular(sys; atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ)
```

Return `true` if the descriptor system `sys = (A-λE,B,C,D)` has a regular pole pencil `A-λE` and `false` otherwise.  

To test whether the pencil `A-λE` is regular (i.e., `det(A-λE) ̸≡ 0`),   the underlying computational procedure reduces the pencil `A-λE` to an appropriate Kronecker-like form,  which provides information on the rank of `A-λE`. 

The keyword arguements `atol1`, `atol2` and `rtol` specify the absolute tolerance for the nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`, and the relative tolerance  for the nonzero elements of `A` and `E`, respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of  `A`, and `ϵ` is the  working machine epsilon.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
