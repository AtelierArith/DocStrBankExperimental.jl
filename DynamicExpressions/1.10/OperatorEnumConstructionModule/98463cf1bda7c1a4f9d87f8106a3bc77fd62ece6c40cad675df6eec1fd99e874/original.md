```
OperatorEnum(; binary_operators=[], unary_operators=[],
               define_helper_functions::Bool=true,
               empty_old_operators::Bool=true)
```

Construct an `OperatorEnum` object, defining the possible expressions. This will also redefine operators for `AbstractExpressionNode` types, as well as `show`, `print`, and `(::AbstractExpressionNode)(X)`. It will automatically compute derivatives with `Zygote.jl`.

# Arguments

  * `binary_operators::Vector{Function}`: A vector of functions, each of which is a binary operator.
  * `unary_operators::Vector{Function}`: A vector of functions, each of which is a unary operator.
  * `define_helper_functions::Bool=true`: Whether to define helper functions for creating  and evaluating node types. Turn this off when doing precompilation. Note that these  are *not* needed for the package to work; they are purely for convenience.
  * `empty_old_operators::Bool=true`: Whether to clear the old operators.
