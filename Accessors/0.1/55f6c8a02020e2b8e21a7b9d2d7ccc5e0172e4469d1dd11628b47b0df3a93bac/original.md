```
@modify(f, obj_optic)
```

Define an optic and call [`modify`](@ref) on it.

```jldoctest
julia> using Accessors

julia> xs = (1,2,3);

julia> ys = @modify(xs |> Elements() |> If(isodd)) do x
           x + 1
       end
(2, 2, 4)
```

Supports the same syntax as [`@optic`](@ref). See also [`@set`](@ref).
