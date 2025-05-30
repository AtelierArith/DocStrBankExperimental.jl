```
PlusEq{FT} <: Function
PlusEq(f)
```

`out += f(args...)` 命令を実行するときに呼び出されます。次の2つの文は同じです。

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
