```
map_coefficients_inplace!(f::Function, a::GenericQuadExpr)
```

Apply `f` to the coefficients and constant term of an [`GenericQuadExpr`](@ref) `a` and update them in-place.

See also: [`map_coefficients`](@ref)

## Example

```jldoctest; setup=:(using JuMP; model = Model(); @variable(model, x))
julia> a = @expression(model, x^2 + x + 1)
x² + x + 1

julia> map_coefficients_inplace!(c -> 2 * c, a)
2 x² + 2 x + 2

julia> a
2 x² + 2 x + 2
```
