```
delete(obj, optic)
```

Delete a part according to `optic` of `obj`.

Note that `optic(delete(obj, optic))` can still have a valid value: for example, when deleting an element from a `Tuple` or `Vector`.

```jldoctest
julia> using Accessors

julia> obj = (a=1, b=2); lens=@optic _.a;

julia> obj_d = delete(obj, lens)
(b = 2,)

julia> lens(obj_d)
ERROR: type NamedTuple has no field a


julia> obj = (1, 2); lens=first;

julia> obj_d = delete(obj, lens)
(2,)

julia> lens(obj_d)
2
```

See also [`set`](@ref), [`insert`](@ref).
