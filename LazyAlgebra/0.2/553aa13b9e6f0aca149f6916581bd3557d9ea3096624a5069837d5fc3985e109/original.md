```
unveil(A)
```

unveils the mapping embedded in mapping `A` if it is a *decorated* mapping (see [`LazyAlgebra.DecoratedMapping`](@ref)); otherwise, just returns `A` if it is not a *decorated* mapping.

As a special case, `A` may be an instance of `LinearAlgebra.UniformScaling` and the result is the LazyAlgebra mapping corresponding to `A`.
