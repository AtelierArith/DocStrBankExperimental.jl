```
(D,V)=get_deflated_eigpairs(S,V,n)
(D,V)=get_deflated_eigpairs(dnep::DeflatedNEP [λ,v])
```

Returns a vector of eigenvalues `D` and a matrix with corresponding eigenvectors `V` of the invariant pair `S,V`. The eigenpairs correspond to the original problem, underlying the `DeflatedNEP`. The optional parameters `λ,v` allows the inclusion of an additional eigpair. Essentially, the optional parameters are the expanding the deflation and the running `get_deflated_eigpairs`  with kwarg, i.e.,

```julia
(D,V)=get_deflated_eigpairs(deflate_eigpair(dnep,λ,v))`
```

See example in [`deflate_eigpair`](@ref).
