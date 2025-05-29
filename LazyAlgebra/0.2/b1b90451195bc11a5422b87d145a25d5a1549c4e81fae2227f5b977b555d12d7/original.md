```
Gram(A) -> obj
```

yields an object instance `obj` representing the composition `A'*A` for the linear mapping `A`.

Directly calling this constructor is discouraged, call [`gram(A)`](@ref) or use expression `A'*A` instead and benefit from automatic simplification rules.

Call [`unveil(obj)`](@ref) to reveal the linear mapping `A` embedded in `obj`.

See also [`gram`](@ref), [`unveil`](@ref) and [`DecoratedMapping`](@ref).
