```
@show_texpr(expr, linenums=false)
```

もう一つの `@show_sexpr` です。 `expr` のリスプスタイルのS式を表示し、`linenums` がtrueの場合は行番号ノードを印刷します。

注: インデントは `@show_sexpr` と異なります。

## 例

```julia
julia> @show_texpr 2x+1
(:call, :+, 
    (:call, :*, 2, :x), 1)
```

`teval` 関数は `@show_texpr` の出力を評価できます。

```julia
julia> x = 10; (:call, :+, 
    (:call, :*, 2, :x), 1) |> teval
21
```
