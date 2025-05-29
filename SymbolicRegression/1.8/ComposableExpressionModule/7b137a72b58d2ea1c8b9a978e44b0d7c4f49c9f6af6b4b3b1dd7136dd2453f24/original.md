```
ValidVector{A<:AbstractVector}
```

A wrapper for an AbstractVector paired with a validity flag (valid::Bool). It represents a vector along with a boolean indicating whether the data is valid. This is useful in computations where certain operations might produce invalid data (e.g., division by zero), allowing the validity to propagate through calculations. Operations on `ValidVector` instances automatically handle the valid flag: if all operands are valid, the result is valid; if any operand is invalid, the result is marked invalid.

You will need to work with this to do highly custom operations with `ComposableExpression` and `TemplateExpression`.

# Fields:

  * `x::A`: The vector data.
  * `valid::Bool`: Indicates if the data is valid.
