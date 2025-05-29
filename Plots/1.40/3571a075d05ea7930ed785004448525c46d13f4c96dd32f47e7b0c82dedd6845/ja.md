```
histogram2d(x,y)
histogram2d!(x,y)
```

2次元ヒストグラムをプロットします。

# 引数

  * `bins`: ビンの数（`Integer`の場合）またはビンのエッジ（`AbtractVector`の場合）
  * `weights`: `x`の値に対する重みのベクトル。`x`の各エントリは、そのビンの高さに重みを寄与します。

# 例

```julia-repl
julia> histogram2d(randn(10_000),randn(10_000))
```
