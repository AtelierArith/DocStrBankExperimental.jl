```
map_coefficients_inplace!(f::Function, a::GenericAffExpr)
```

Apply `f` to the coefficients and constant term of an [`GenericAffExpr`](@ref) `a` and update them in-place.

See also: [`map_coefficients`](@ref)

## Example

```jldoctest; setup=:(using JuMP; model = Model(); @variable(model, x))
julia> a = GenericAffExpr(1.0, x => 1.0)
x + 1

julia> map_coefficients_inplace!(c -> 2 * c, a)
2 x + 2

julia> a
2 x + 2
```
