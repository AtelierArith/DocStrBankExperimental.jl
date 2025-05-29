```
isunimodular(A, E; atol1::Real = 0, atol2::Real = 0, rtol::Real=min(atol1,atol2)>0 ? 0 : n*ϵ) -> Bool
```

Test whether the matrix pencil `A-λE` is unimodular (i.e., `A-λE` is square, regular and `det(A-λE) == constant`).  The underlying computational procedure reduces the pencil `A-λE` to an appropriate Kronecker-like form,  which provides information to check the full rank of `A-λE` and the lack of finite eigenvalues. 

The keyword arguements `atol1`, `atol2` and `rtol` specify the absolute tolerance for the nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`, and the relative tolerance  for the nonzero elements of `A` and `E`, respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of  `A`, and `ϵ` is the  machine epsilon of the element type of `A`. 
