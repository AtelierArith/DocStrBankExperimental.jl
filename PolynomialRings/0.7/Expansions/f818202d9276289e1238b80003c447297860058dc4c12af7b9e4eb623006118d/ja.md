```
@constant_coefficient(f, vars...)
```

`f`の定数係数を`vars`の関数として返します。

!!! note
    `vars`はリテラル変数名である必要があります; それを含む変数ではありません。


# 例

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> @constant_coefficient(x^3*y + x + y + 1, x)
y + 1

julia> @constant_coefficient(x^3*y + x + y + 1, x, y)
1
```

# 参照

`constant_coefficient`、`@coefficient`、および`@expansion`
