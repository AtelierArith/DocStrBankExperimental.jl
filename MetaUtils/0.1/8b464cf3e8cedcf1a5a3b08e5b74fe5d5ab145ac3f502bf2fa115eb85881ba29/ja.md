```
@show_sexpr(expr, linenums=false)
```

は `expr` のリスプスタイルのS式を表示し、`linenums` が true の場合は行番号ノードを印刷します。これは `Meta.show_sexpr` のマクロ版です。

## 例

```julia
julia> @show_sexpr 2x+1
(:call, :+, (:call, :*, 2, :x), 1)
```

`teval` 関数は `@show_sexpr` の出力を評価できます。

```julia
julia> x = 10; (:call, :+, (:call, :*, 2, :x), 1) |> teval
21
```
