```
csa_forecast_plot(x::Array, h::Int, p::Real, q::Real)
```

CSA法を使用して長期記憶時系列の予測をプロットします。

# 引数

  * `x::Array`: 時系列。
  * `h::Int`: 予測する期間の数。
  * `p::Real`: CSAプロセスのパラメータp。
  * `q::Real`: CSAプロセスのパラメータq。

# 出力

  * `p1::Plot`: 元の時系列と予測のプロット。

# 注意事項

複数のディスパッチを使用して、信頼区間の有無にかかわらず時系列の予測をプロットします。プロットは`csa_forecast`関数を呼び出すことで行われます。

# 例

```julia
julia> csa_forecast_plot(csa_gen(100,1.4,1.4), 10, 1.4, 1.4)
```
