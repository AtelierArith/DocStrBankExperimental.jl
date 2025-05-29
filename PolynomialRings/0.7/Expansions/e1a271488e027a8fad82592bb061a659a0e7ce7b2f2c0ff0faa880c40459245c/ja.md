```
constant_coefficient(f, vars...)
```

`f`の定数係数を`vars`の関数として返します。

!!! note
    `vars`はシンボルである必要があります。例えば、多項式`x`ではありません。


# 例

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> constant_coefficient(x^3*y + x + y + 1, :x)
y + 1

julia> constant_coefficient(x^3*y + x + y + 1, :x, :y)
1
```

# 参照

`@constant_coefficient`、`@coefficient`、および`@expansion`
