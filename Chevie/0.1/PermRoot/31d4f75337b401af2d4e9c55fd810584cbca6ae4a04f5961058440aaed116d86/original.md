`PermY(W::ComplexReflectionGroup,M::AbstractMatrix)`

Let  `M`  be  an  invertible  linear  map  on  the  dual  of the reflection representation  of `W` which  preserves the set  of coroots of `parent(W)`, and  normalizes  `W`  (for  the  action  of matrices on the right). `PermY` returns  the corresponding  permutation of  the coroots  of `parent(W)`; it returns  `nothing`  if  `M`  does  not  normalize  the  set  of  coroots of `parent(W)`.

```julia-repl
julia> W=reflection_subgroup(rootdatum("E7sc"),1:6)
E₇₍₁₂₃₄₅₆₎=E₆Φ₁

julia> PermY(W,YMatrix(W,longest(W)))==longest(W)
true
```
