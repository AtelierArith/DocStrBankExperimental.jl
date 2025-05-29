```
map_coefficients(f::Function, a::GenericQuadExpr)
```

Apply `f` to the coefficients and constant term of an [`GenericQuadExpr`](@ref) `a` and return a new expression.

See also: [`map_coefficients_inplace!`](@ref)

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> a = @expression(model, x^2 + x + 1)
x² + x + 1

julia> map_coefficients(c -> 2 * c, a)
2 x² + 2 x + 2

julia> a
x² + x + 1
```
