```
modify(f, obj, optic)
```

Replace a part `x` of `obj` by `f(x)`. The `optic` argument selects which part to replace.

```jldoctest
julia> using Accessors

julia> obj = (a=1, b=2); optic=@optic _.a; f = x -> "hello $x";

julia> modify(f, obj, optic)
(a = "hello 1", b = 2)
```

See also [`set`](@ref).
