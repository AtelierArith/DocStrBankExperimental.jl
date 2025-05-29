```
Scenario{op,pl_op,pl_fun}
```

Store a testing scenario composed of a function and its input + output for a given operator.

This generic type should never be used directly: use the specific constructor corresponding to the operator you want to test, or a predefined list of scenarios.

# Type parameters

  * `op`: one  of `:pushforward`, `:pullback`, `:derivative`, `:gradient`, `:jacobian`,`:second_derivative`, `:hvp`, `:hessian`
  * `pl_op`: either `:in` (for `op!(f, result, backend, x)`) or `:out` (for `result = op(f, backend, x)`)
  * `pl_fun`: either `:in` (for `f!(y, x)`) or `:out` (for `y = f(x)`)

# Constructors

```
Scenario{op,pl_op}(
    f, x, [t], contexts...;
    prep_args, res1, res2, name
)

Scenario{op,pl_op}(
    f!, y, x, [t,] contexts...;
    prep_args, res1, res2, name
)
```

Default values:

  * `prep_args =` the result of `zero` applied to each execution argument
  * `res1 = res2 = nothing`
  * `name = nothing`

# Fields

  * `f::Any`: function `f` (if `pl_fun==:out`) or `f!` (if `pl_fun==:in`) to apply
  * `y::Any`: primal output
  * `x::Any`: primal input
  * `t::Union{Nothing, NTuple{N, T} where {N, T}}`: tangents (if applicable)
  * `contexts::Tuple`: contexts (if applicable)
  * `res1::Any`: first-order result of the operator (if applicable)
  * `res2::Any`: second-order result of the operator (if applicable)
  * `prep_args::NamedTuple`: named tuple of arguments passed to preparation, without the function - the required keys are a subset of `(; y, x, t, contexts)` depending on the operator
  * `name::Union{Nothing, String}`: name of the scenario for display in test sets and dataframes
