```
@unitgroup(U::UnitSystem,S::UnitSystem) -> (u::typeof(normal(U)))(d::Group) = normal(S)(d)
```

Implements `Group` homomorphism for `U` in terms of existing specification from `S`.
