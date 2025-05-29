```
@latexrun expression
```

式をLaTeX形式に変換して評価します。代入のような副作用を持つ式に便利です。

# 例

```julia-repl
julia> @latexrun y = 3/2 + $(3/2)
L"$y = \frac{3}{2} + 1.5$"

julia> y
3.0
```

[`@latexify`](@ref)や[`@latexdefine`](@ref)も参照してください。
