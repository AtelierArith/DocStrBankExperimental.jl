```
IsExplicitDecorator <: AbstractTrait
```

Specify that a certain type should dispatch per default to its [`decorated_manifold`](@ref).

!!! note
    Any decorator *behind* this decorator might not have any effect, since the function dispatch is moved to its field at this point. Therefore this decorator should always be *last* in the [`TraitList`](@ref).

