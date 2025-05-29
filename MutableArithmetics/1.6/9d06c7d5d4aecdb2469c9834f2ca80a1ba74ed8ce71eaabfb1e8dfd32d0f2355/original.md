```
buffered_operate_to!(buffer, output, op::Function, args...)
```

Modify the value of `output` to be equal to the value of `op(args...)`, possibly modifying `buffer`. Can only be called if `mutability(output, op, args...)` returns [`IsMutable`](@ref).
