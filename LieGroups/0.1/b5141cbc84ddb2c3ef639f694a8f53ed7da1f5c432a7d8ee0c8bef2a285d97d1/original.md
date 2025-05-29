```
AdditionGroupOperation <: AbstractGroupOperation
```

A group operation that is realised introducing defaults that fall back to `+` and `-` being overloaded, for example `_compose(G::LieGroup{𝔽,AdditionGroupOperation}, a, b) = a + b`
