```
substitute(expr, s; fold=true)
```

`expr`に対してルール`s`に従って置換を行います。`fold=false`の場合、評価可能な式は評価されません。

# 例

```jldoctest
julia> @variables t x y z(t)
4-element Vector{Num}:
    t
    x
    y
 z(t)
julia> ex = x + y + sin(z)
(x + y) + sin(z(t))
julia> substitute(ex, Dict([x => z, sin(z) => z^2]))
(z(t) + y) + (z(t) ^ 2)
julia> substitute(sqrt(2x), Dict([x => 1]); fold=false)
sqrt(2)
```
