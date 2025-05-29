```
@linear_coefficient(f, vars...)
linear_coefficients(f, vars...)
```

`f`の線形係数を`vars`の関数として返します。

!!! note
    `vars`はシンボルである必要があります。例えば、ポリノミアル`x`ではありません。


# 例

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> @linear_coefficients(x^3*y + x + y + 1, x)
1-element Array{@ring(ℤ[y]),1}:
 1

julia> @linear_coefficients(x^3*y + x + y + 1, x, y)
2-element Array{BigInt,1}:
 1
 1
```

# 参照

`@constant_coefficient`、`@coefficient`、および`@expansion`
