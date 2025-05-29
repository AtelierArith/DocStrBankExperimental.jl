```
@rewrite(expr, move_factors_into_sums = true)
```

Return the value of `expr`, exploiting the mutability of the temporary expressions created for the computation of the result.

If you have an `Expr` as input, use [`rewrite_and_return`](@ref) instead.

See [`rewrite`](@ref) for an explanation of the keyword argument.

!!! info
    Passing `move_factors_into_sums` after a `;` is not supported. Use a `,` instead.

