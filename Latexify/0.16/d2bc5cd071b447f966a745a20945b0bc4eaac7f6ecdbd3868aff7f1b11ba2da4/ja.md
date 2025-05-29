```
@latexify 式
```

`式`を表す`LaTeXString`を作成します。変数や式は`$`で補間できます。キーワード引数は引数に追加することで`latexify`に供給できます。

# 例

```julia-repl
julia> @latexify x^2 + 3/2
L"$x^{2} + \frac{3}{2}$"

julia> @latexify x^2 + $(3/2)
L"$x^{2} + 1.5$"

julia> @latexify x^2 + 3/2 env=:raw
L"x^{2} + \frac{3}{2}"
```

[`latexify`](@ref)、[`@latexrun`](@ref)、[`@latexdefine`](@ref)も参照してください。
