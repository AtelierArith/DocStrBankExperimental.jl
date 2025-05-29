```
to_same_concrete_type(Ts::Type...) -> T::Type
```

yields `T = promote_type(Ts...)` throwing an exception if `T` is not a concrete type.

Also see [`to_same_type`](@ref).
