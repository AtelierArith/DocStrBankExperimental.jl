```
isregular(A, E, γ; atol::Real = 0,  rtol::Real = atol > 0 ? 0 : n*ϵ) -> Bool
```

Test whether the matrix pencil `A-λE` is regular at `λ = γ` (i.e., `A-λE` is square and ${\small\det(A-λE) \neq 0}$).  The underlying computational procedure checks the maximal rank of `A-γE` if `γ` is finite and of `E` if  `γ` is infinite . 

The keyword arguements `atol` and `rtol` specify the absolute and relative tolerances for the nonzero elements of `A-γE`, respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of  `A`, and `ϵ` is the  machine epsilon of the element type of `A`. 
