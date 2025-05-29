```
component(::Type{Field}, A::AbstractAssociativeAlgebra, i::Int)
  -> Vector{Tuple{Field, Morphism}}
```

Given an étale algebra $A$ and index $i$, return the $i$-th simple components of $A$ as a field $K$ together with the projection $A \to K$.
