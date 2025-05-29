```
map_coefficients(f::Function, a::GenericAffExpr)
```

Apply `f` to the coefficients and constant term of an [`GenericAffExpr`](@ref) `a` and return a new expression.

See also: [`map_coefficients_inplace!`](@ref)

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> a = GenericAffExpr(1.0, x => 1.0)
x + 1

julia> map_coefficients(c -> 2 * c, a)
2 x + 2

julia> a
x + 1
```
