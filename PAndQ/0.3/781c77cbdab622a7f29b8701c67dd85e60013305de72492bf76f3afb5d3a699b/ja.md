```
@variables(ps...)
```

変数を定義し、それらを含む `Vector` を返します。

例

```jldoctest
julia> @variables p q
2-element Vector{PAndQ.Variable}:
 p
 q

julia> p
p

julia> q
q
```
