```
rescaled_range_plot(x::Array; k::Int = 100, slope::Bool = false, slope2::Bool = false)
```

時系列の再スケーリング範囲プロットを生成します。

# 引数

  * `x::Array`: 時系列。

# 出力

  * `p1::Plots.Plot`: 再スケーリング範囲プロット。

# オプション引数

  * `k::Int`: 時系列の分割数。デフォルトは100。
  * `slope::Bool`: trueの場合、線形回帰の傾きが表示されます。
  * `slope2::Bool`: trueの場合、短期記憶プロセスの理論的な傾きが表示されます。

# 注意事項

この関数は、再スケーリング範囲の対数に対して線形回帰法を使用して長期記憶パラメータを推定します。ハースト係数は、式 H = d + 1/2 によって長期記憶パラメータ d に関連しています。

# 例

```julia
julia> rescaled_range_plot(randn(300,1))
```
