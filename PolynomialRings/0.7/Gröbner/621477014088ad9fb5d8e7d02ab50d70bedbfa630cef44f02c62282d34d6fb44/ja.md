```
syz = syzygies(G)
```

Gの要素間のすべての関係を返します。

# 例

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> I = [x^5, x^2 + y, x*y + y^2];

julia> G, tr = gröbner_transformation(I);

julia> K = syzygies(G) * tr; # これらの生成子によって誘導されるマップ R^3 -> I のカーネル

julia> iszero(K * I)
true
```
