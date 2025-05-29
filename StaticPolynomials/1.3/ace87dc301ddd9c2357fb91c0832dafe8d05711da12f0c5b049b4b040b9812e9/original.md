```
PolynomialSystem{N, NVars, NParams, <:Tuple}
```

A polynomial system of `N` polynomials in `NVars` variables with `NParams` variables.

Constructors:

```
PolynomialSystem(polys::AbstractVector{<:MP.AbstractPolynomial}; variables=MP.variables(polys), parameters=nothing)
PolynomialSystem(polys::MP.AbstractPolynomial...; kwargs...)
```

Create a system of polynomials from the given polynomials `polys`. This function is by design not typestable.

## Example

```julia
julia> import DynamicPolynomials: @polyvar
julia> @polyvar x y a
julia> PolynomialSystem(x^2+y^2+3, x-y+2, x^2+2y+a; parameters=[a])
PolynomialSystem{3, 2}:
 3 + x² + y²

 2 + x - y

 x² + 2y

```
