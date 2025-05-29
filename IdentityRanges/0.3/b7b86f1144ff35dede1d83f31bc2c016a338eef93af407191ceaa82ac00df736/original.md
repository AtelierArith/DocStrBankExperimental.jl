```
IdentityRange(start, stop) -> idr
IdentityRange(r::AbstractUnitRange) -> idr
```

Defines an `AbstractUnitRange` where `idr[i] == i` for any valid `i`, or equivalently `axes(idr, 1)` returns a range with the same values as present in `idr`.

These are particularly useful for creating `view`s of arrays that preserve the supplied axes:

```jldoctest
julia> a = rand(8);

julia> v1 = view(a, 3:5);

julia> axes(v1, 1)
Base.OneTo(3)

julia> idr = IdentityRange(3:5)
IdentityRange(3:5)

julia> v2 = view(a, idr);

julia> axes(v2, 1)
3:5
```
