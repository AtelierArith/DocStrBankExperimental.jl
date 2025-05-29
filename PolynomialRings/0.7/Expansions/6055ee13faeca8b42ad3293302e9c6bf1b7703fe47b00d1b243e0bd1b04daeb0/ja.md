```
@deg(f, vars...)
```

与えられた変数において多項式として展開されたときの `f` の総次数を返します。

!!! note
    `vars` はリテラル変数名である必要があります; それを含む変数ではいけません。


# 例

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> @deg (x^2 + x*y - 1) x
2

julia> @deg (x^2 + x*y - 1) y
1
```

# 参照

`deg`, `@expansion` ```
