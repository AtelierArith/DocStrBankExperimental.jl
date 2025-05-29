```
normalize(x::Decimal)
```

Return an equal number reduced to its simplest form with all trailing zeros in the coefficient removed.

# Examples

```jldoctest
julia> x = dec"1.2000"
1.2000

julia> x.c # Coefficient of `x`
12000

julia> y = normalize(dec"1.2000")
1.2

julia> y.c # Coefficient of `y`
12

julia> x == y
true
```
