```
hspan(y)
```

位置 `y[1]` の水平線と位置 `y[2]` の水平線の間に矩形を描画します。`length(y) ≥ 4` の場合、さらに `y[3]` と `y[4]`、`y[5]` と `y[6]` の間に矩形が描画されます。`length(y)` が奇数の場合、`y` の最後のエントリは無視されます。

# 例

```julia-repl
julia> hspan(1:6)
```
