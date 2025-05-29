```
pull_vars(::Num)
pull_vars(::Vector{Num})
pull_vars(::Equation)
pull_vars(::Vector{Equation})
```

Pull out all variables/symbols from an expression or the RHS of an equation (or RHSs of a set of equations), and sort them. Variables are sorted alphabetically, then in the order [cv, cc, L, U], then followed by the terms for the subgradient of the convex relaxation and terms for  the subgradient of the concave relaxation.

# Example

```julia> @variables out, x, y, z
julia> func = out ~ z + 2*y - 3*x*z
julia> pull_vars(func)
3-element Vector{Num}:
 x
 y
 z
```
