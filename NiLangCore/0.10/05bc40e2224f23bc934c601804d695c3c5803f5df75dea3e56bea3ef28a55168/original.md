```
PlusEq{FT} <: Function
PlusEq(f)
```

Called when executing `out += f(args...)` instruction. The following two statements are same

```jldoctest; setup=:(using NiLangCore)
julia> x, y, z = 0.0, 2.0, 3.0
(0.0, 2.0, 3.0)

julia> x, y, z = PlusEq(*)(x, y, z)
(6.0, 2.0, 3.0)

julia> x, y, z = 0.0, 2.0, 3.0
(0.0, 2.0, 3.0)

julia> @instr x += y*z


julia> x, y, z
(6.0, 2.0, 3.0)
```
