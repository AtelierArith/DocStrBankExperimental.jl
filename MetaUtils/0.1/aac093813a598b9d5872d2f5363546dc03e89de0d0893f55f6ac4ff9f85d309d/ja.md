```
@show_expr(expr, linenums=false)
```

は、`expr`のJuliaスタイルの式を表示し、`linenums`がtrueの場合は行番号ノードを印刷します。これは`show_expr`のマクロバージョンです。

## 例

```julia
julia> @show_expr 2x+1
Expr(:call, :+, 
    Expr(:call, :*, 2, :x), 1)
```

`eval`関数は`@show_expr`の出力を評価できます。

```julia
julia> x = 10; Expr(:call, :+, 
    Expr(:call, :*, 2, :x), 1) |> eval
21
```
