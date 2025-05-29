```
mutability(T::Type, ::typeof(op), args::Type...)::MutableTrait
```

Return either [`IsMutable`](@ref) to indicate an object of type `T` can be modified to be equal to `op(args...)` or [`IsNotMutable`](@ref) otherwise.
