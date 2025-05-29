```
is_subset(a::MPolyQuoIdeal{T}, b::MPolyQuoIdeal{T}) where T
```

`a` が `b` に含まれている場合は `true` を返し、そうでない場合は `false` を返します。

# 例

```jldoctest
julia> R, (x, y) = polynomial_ring(QQ, [:x, :y]);

julia> A, _ = quo(R, ideal(R, [x^3*y^2-y^3*x^2, x*y^4-x*y^2]));

julia> a = ideal(A, [x^3*y^4-x+y, x*y+y^2*x])
理想は次のもので生成されます
  x^3*y^4 - x + y
  x*y^2 + x*y

julia> b = ideal(A, [x^3*y^3-x+y, x^2*y+y^2*x])
理想は次のもので生成されます
  x^3*y^3 - x + y
  x^2*y + x*y^2

julia> is_subset(a,b)
false

julia> is_subset(b,a)
true
```
