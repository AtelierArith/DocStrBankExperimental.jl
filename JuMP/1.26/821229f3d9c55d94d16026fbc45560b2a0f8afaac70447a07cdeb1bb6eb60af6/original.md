```
isequal_canonical(
    x::T,
    y::T
) where {T<:AbstractJuMPScalar,AbstractArray{<:AbstractJuMPScalar}}
```

Return `true` if `x` is equal to `y` after dropping zeros and disregarding the order.

This method is mainly useful for testing, because fallbacks like `x == y` do not account for valid mathematical comparisons like `x[1] + 0 x[2] + 1 == x[1] + 1`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> a = x[1] + 1.0
x[1] + 1

julia> b = x[1] + x[2] + 1.0
x[1] + x[2] + 1

julia> add_to_expression!(b, -1.0, x[2])
x[1] + 0 x[2] + 1

julia> a == b
false

julia> isequal_canonical(a, b)
true
```
