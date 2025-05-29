```
isregular(A, E; atol1::Real = 0, atol2::Real = 0, rtol::Real=min(atol1,atol2)>0 ? 0 : n*ϵ) -> Bool
```

Test whether the matrix pencil `A-λE` is regular (i.e., `A-λE` is square and ${\small\det(A-λE) \not\equiv 0}$).  The underlying computational procedure reduces the pencil `A-λE` to an appropriate Kronecker-like form,  which provides information on the rank of `A-λE`. 

The keyword arguements `atol1`, `atol2` and `rtol` specify the absolute tolerance for the nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`, and the relative tolerance  for the nonzero elements of `A` and `E`, respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of  `A`, and `ϵ` is the  machine epsilon of the element type of `A`. 
