```
@expand(f, var, [var...])
```

fをその構成要素に分解する（指数タプル、係数）のタプルのコレクションを返します。

# 例

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> collect(@expand(x^3 + y^2, y))
2-element Array{Tuple{Tuple{Int16},@ring(ℤ[x])},1}:
 ((0,), x^3)
 ((2,), 1)

julia> collect(@expand(x^3 + y^2, x, y))
2-element Array{Tuple{Tuple{Int16,Int16},BigInt},1}:
 ((0, 2), 1)
 ((3, 0), 1)
```

# 参照

`@expansion`、`expand(...)`、`@coefficient` および `coefficient`
