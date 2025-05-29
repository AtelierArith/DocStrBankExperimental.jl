```
operate_to!(output, op::Function, args...)
```

Modify the value of `output` to be equal to the value of `op(args...)`. Can only be called if `mutability(output, op, args...)` returns [`IsMutable`](@ref).

If `output === args[i]` for some `i`, this function may throw an error. Use `operate!!` or `operate!` instead.

For example, in DynamicPolynomials, `operate_to!(p, +, p, q)` throws an error because otherwise, the algorithm would fill `p` while iterating over the terms of `p` and `q` hence it will never terminate. On the other hand `operate!(+, p, q)` uses a different algorithm that efficiently inserts the terms of `q` in the sorted list of terms of `p` with minimal displacement.
