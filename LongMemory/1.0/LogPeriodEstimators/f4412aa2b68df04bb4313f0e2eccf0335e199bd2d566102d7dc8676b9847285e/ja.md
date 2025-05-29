```
periodogram_plot(x::Array; slope::Bool=true)
```

時系列 `x` の対数周期グラムをプロットします。

# 引数

  * `x::Vector`: 時系列

# 出力

  * `p1::Plots.Plot`: 対数周期グラム

# オプション引数

  * `slope::Bool`: true の場合、線形回帰の傾きが表示されます。

# 例

```julia-repl
julia> periodogram_plot(randn(100,1))
```
