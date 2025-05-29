```
@polynomial x^3 + 3x^2 + 3x + 1
```

式から多変数多項式を作成するには、式に現れるすべての記号によって生成される環を作成します。

# 例

```jldoctest
julia> using PolynomialRings

julia> @polynomial x^3 + x^2*y + x*y^2 + y^3
x^3 + x^2*y + x*y^2 + y^3

julia> @polynomial x^3 + x^2*y + x*y^2 + y^3
x^3 + x^2*y + x*y^2 + y^3
```

!!! 注     一般に、マクロ式の外部から変数を使用することはできません。すべての記号は変数として解釈されます。例えば：

````
```
d = 4
@polynomial d*x
```

は、2つの変数 `d` と `x` の多項式を返します。

特別な例外として、指数は解釈されないため、

```
@polynomial(x^d) == @polynomial(x)^d
```

残念ながら/混乱を招くことに、これにより

```
@polynomial(d*x^(d-1))
```

は `d-1` が `d` を外部変数として解釈し、`d*x` は単項式になります。

この動作は（変わるべき？）変わるかもしれません。
````

# 参照

`@ring`, `polynomial_ring`, `convert(R, symbol)`
