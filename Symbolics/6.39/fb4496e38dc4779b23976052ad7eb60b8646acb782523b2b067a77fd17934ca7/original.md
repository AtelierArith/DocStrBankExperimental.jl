```julia
expand_derivatives(O; ...)
expand_derivatives(O, simplify; throw_no_derivative)

```

Expands derivatives within a symbolic expression `O`.

This function recursively traverses a symbolic expression, applying the chain rule and other derivative rules to expand any derivatives it encounters.

# Arguments

  * `O::Symbolic`: The symbolic expression to expand.
  * `simplify::Bool=false`: Whether to simplify the resulting expression using   [`SymbolicUtils.simplify`](@ref).

# Keyword Arguments

  * `throw_no_derivative=false`: Whether to throw if a function with unknown  derivative is encountered.

# Examples

```jldoctest
julia> @variables x y z k;

julia> f = k*(abs(x-y)/y-z)^2
k*((abs(x - y) / y - z)^2)

julia> Dx = Differential(x) # Differentiate wrt x
(::Differential) (generic function with 2 methods)

julia> dfx = expand_derivatives(Dx(f))
(k*((2abs(x - y)) / y - 2z)*ifelse(signbit(x - y), -1, 1)) / y
```
