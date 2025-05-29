```
check_derivatives(f, x=rand())
```

Checks (using assertions) that the derivatives of f agree (up to the square root of machine precision)  with those computed by TaylorSeries.

This is a useful sanity check if you redefine derivatives.

The derivative are checked in a point `x` (default: rand()), which should be in the domain of `f`.

# ```jldoctest

# julia> f = @define*with*derivatives x->x^2 x->2x x->2;

# ERROR: LoadError: UndefVarError: `@define_with_derivatives` not defined

# in expression starting at none:1

# julia> check_derivatives(f, 0.2)

# ERROR: UndefVarError: `check_derivatives` not defined

# Stacktrace:

# [1] top-level scope

# @ none:1

# julia> g = @define*with*derivatives x->x^2 x->2x x->3;

# ERROR: LoadError: UndefVarError: `@define_with_derivatives` not defined

# in expression starting at none:1

# julia> check_derivatives(g, 0.2)

# ERROR: UndefVarError: `check_derivatives` not defined

# Stacktrace:

# [1] top-level scope

# @ none:1

# ```
