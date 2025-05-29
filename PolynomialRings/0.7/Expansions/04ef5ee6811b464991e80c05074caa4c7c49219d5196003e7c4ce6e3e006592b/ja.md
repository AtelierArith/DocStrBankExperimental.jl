```
coefficient(f, exponent_tuple, symbol, [symbol...])
```

fのモノミアルにおける係数を返します。REPLでは、より使いやすいバージョン`@coefficient`を使用することをお勧めします。

# 例

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> coefficient(x^3*y + x, (1,), :x)
1

julia> coefficient(x^3*y + x, (3,), :x)
y

julia> coefficient(x^3*y + x, (3,0), :x, :y)
0

julia> coefficient(x^3*y + x, (3,1), :x, :y)
1
```

# 参照

`@coefficient`、`expansion`および`@expansion`
