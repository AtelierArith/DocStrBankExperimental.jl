```
deg(f, vars...)
```

`vars`を変数と見なしたときの`f`の総次数を返します。ゼロ多項式の場合は-1を返します。

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> deg(x^2, :x)
2

julia> deg(x^2, :x, :y)
2

julia> deg(x^2, :y)
0
```
