```
ZZ2 <: Number
```

A type representing integers modulo 2.

Elements can be created via the functions `zero` and `one` or from an argument of type `Bool` or any other `Integer` type. More generally, any argument accepted by `isodd` can be converted to `ZZ2`. In algebraic computations with `ZZ2`, `Integer` types are promoted to `ZZ2`. Conversely, elements of type `ZZ2` can be converted to `Bool`.

See also `Base.zero`, `Base.one`, `Base.iszero`, `Base.isone`, `Base.isodd`.

# Examples

```jldoctest
julia> ZZ2(1) == one(ZZ2)
true

julia> iszero(ZZ2(4.0))
true

julia> x = ZZ2(1) + 3
0

julia> typeof(x)
ZZ2

julia> Bool(x), convert(Bool, x)
(false, false)
```
