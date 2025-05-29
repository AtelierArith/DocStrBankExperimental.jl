```
@latexdefine expression
```

`expression`をLaTeX形式に変換し、等号とその評価結果を続けて表示します。代入のような式の副作用も評価されます。RHSは、キーワード引数`post`として関数を指定することでフォーマットまたは変換できます。

# 例

```julia-repl
julia> @latexdefine y = 3/2 + $(3/2) env=:equation
L"\begin{equation}
y = \frac{3}{2} + 1.5 = 3.0
\end{equation}
"

julia> y
3.0

julia> @latexdefine y=π post=round
L"$x = \pi = 3.0$"
```

他にも[`@latexify`](@ref)、[`@latexrun`](@ref)を参照してください。
