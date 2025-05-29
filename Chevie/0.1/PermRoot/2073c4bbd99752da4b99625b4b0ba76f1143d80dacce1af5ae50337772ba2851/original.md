`reflection_length(W::PermRootGroup,w::Perm)` or `reflength`

This  function returns the  number of eigenvalues  of `w` in the reflection representation  which are not equal to 1.  For a finite Coxeter group, this is  equal to the  reflection length of  `w`, that is  the minimum number of reflections  of which `w`  is a product.  This also holds  in general for a well-generated  complex reflection group if  `w` divides for the reflection length a Coxeter element.

```julia-repl
julia> W=coxgroup(:A,4)
A₄

julia> reflength(W,longest(W))
2

julia> reflength(W,W(1,2,3,4))
4
```
