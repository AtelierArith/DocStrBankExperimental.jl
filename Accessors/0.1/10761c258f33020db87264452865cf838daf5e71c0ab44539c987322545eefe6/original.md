```
insert(obj, optic, val)
```

Insert a part according to `optic` into `obj` with the value `val`.

For a callable `optic`, this law defines the `insert` operation: `optic(insert(obj, optic, val)) == val` (for an appropriate notion of equality).

```jldoctest
julia> using Accessors

julia> obj = (a=1, b=2); lens=@optic _.c; val = 100;

julia> insert(obj, lens, val)
(a = 1, b = 2, c = 100)
```

See also [`set`](@ref), [`delete`](@ref).
