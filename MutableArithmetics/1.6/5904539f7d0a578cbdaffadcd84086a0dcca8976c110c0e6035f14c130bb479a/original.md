```
operate!(op::Function, args...)
```

Modify the value of `args[1]` to be equal to the value of `op(args...)`. Can only be called if `mutability(args[1], op, args...)` returns [`IsMutable`](@ref).
