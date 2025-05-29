```
get_variables(O) -> Vector{BasicSymbolic}
```

式の中の変数を返します。返される変数は `Num` 型でラップされていないことに注意してください。

# 例

```julia
julia> @variables t x y z(t)
4-element Vector{Num}:
    t
    x
    y
 z(t)

julia> ex = x + y + sin(z)
(x + y) + sin(z(t))

julia> Symbolics.get_variables(ex)
3-element Vector{Any}:
 x
 y
 z(t)
```
