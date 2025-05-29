```
f = @define_with_derivatives(ex1, ex2, ex3)
```

Declares a new function f, and redefines the various functions related to derivatives so that its derivatives are computed with the given expressions.

# ```jldoctest

# julia> f = @define*with*derivatives x->x^2 x->2x x->2;

# ERROR: LoadError: UndefVarError: `@define_with_derivatives` not defined

# in expression starting at none:1

# julia> value*and*derivative(f, 45)

# ERROR: UndefVarError: `value_and_derivative` not defined

# Stacktrace:

# [1] top-level scope

# @ none:1

# ```

Note that the three macro parameters are separated just by spaces (no commas or parentheses)

# ```jldoctest

# julia> g = @define*with*derivatives x->12 x->34 x->56;

# ERROR: LoadError: UndefVarError: `@define_with_derivatives` not defined

# in expression starting at none:1

# julia> value*derivative*and*second*derivative(g, -23.5)

# ERROR: UndefVarError: `value_derivative_and_second_derivative` not defined

# Stacktrace:

# [1] top-level scope

# @ none:1

# ```

This is provided for convenience, but note that in many cases one can find  common subexpressions in a function and its derivatives; hence it is more efficient to define the two functions separately.

If you define derivatives in this way, it is recommended to run `check_derivatives` to ensure that you did not make any mistakes (e.g., forgetting a factor 2). We do not run it automatically because that would require knowing a valid `x` in the domain of `f`.
