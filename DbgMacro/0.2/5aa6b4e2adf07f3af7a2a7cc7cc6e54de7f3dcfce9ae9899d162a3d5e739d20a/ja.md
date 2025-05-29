```
@qn <式>
```

式を返しますが、$ 補間は行いません。

# 例

```jldoctest
julia> @qn foo(1, x, :y, $z)
:(foo(1, x, :y, $(Expr(:$, :z))))
```
