```
log_variance_plot(x::Array; m::Int=100, slope::Bool=false, slope2::Bool=false)
```

時系列のログ分散プロットを生成します。

# 引数

  * `x::Array`: 時系列。

# 出力

  * `d_var::Real`: 推定された長期記憶パラメータで、これは分散プロットのログの線形回帰の傾きβを用いて(betta+1)/2として計算されます。

# オプション引数

  * `m::Int`: 時系列の分割数。デフォルトは20です。m ≈ length(x)/2の値が推奨されます。
  * `slope::Bool`: trueの場合、線形回帰の傾きが表示されます。
  * `slope2::Bool`: trueの場合、短期記憶プロセスの理論的な傾きが表示されます。

# 注意事項

この関数は、長期記憶パラメータを推定するために、分散プロットのログに対して線形回帰法を使用します。

# 例

```julia
julia> log_variance_plot(randn(100,1); m = 40)
```
