```
AbstractMultiplicationGroupOperation <: AbstractGroupOperation
```

A group operation that is realised introducing defaults that fall back to `*` being overloaded, for example `_compose(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, a, b) = a * b`
