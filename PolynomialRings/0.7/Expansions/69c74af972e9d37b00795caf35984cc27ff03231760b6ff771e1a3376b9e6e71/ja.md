```
@coefficient(f, monomial)
```

`f`の`monomial`における係数を返します。

!!! note
    `monomial`はリテラルモノミアルである必要があります。モノミアルを含む変数ではいけません。このマクロは、`monomial`から指数と変数名を取得するかなり単純なパーサーを持っています。

    これは機能と見なされます（バグではありません）。なぜなら、リテラルモノミアルとしてのみ、例えば`x^4`と`x^4*y^0`を区別できるからです。


# 例

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> @coefficient(x^3*y + x, x)
1

julia> @coefficient(x^3*y + x, x^3)
y

julia> @coefficient(x^3*y + x, x^3*y^0)
0

julia> @coefficient(x^3*y + x, x^3*y^1)
1
```

# 参照

`coefficient`、`expansion`および`@expansion`
