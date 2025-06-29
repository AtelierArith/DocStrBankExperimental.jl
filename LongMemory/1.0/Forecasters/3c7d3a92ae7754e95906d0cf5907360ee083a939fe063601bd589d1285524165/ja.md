```
har_forecast_plot(x::Array, h::Int; flag::Bool = true, m::Array=[1,5,22])
```

時系列の予測をプロットし、HARモデルをフィッティングして再帰的に予測します。

# 引数

  * `x::Array`: 時系列。
  * `h::Int`: 予測する期間の数。

# 出力

  * `p1::Plot`: 元の時系列と予測のプロット。

# オプション引数

  * `flag::Bool`: trueの場合、出力は行列で、最初の列が予測、2列目が下側信頼帯、3列目が上側信頼帯です。デフォルトはtrueです。
  * `m::Array`: HARモデルに含めるラグ。デフォルトは[1,5,22]です。

# 注意事項

複数のディスパッチを使用して、信頼帯の有無にかかわらず時系列の予測をプロットします。プロットは`har_forecast`関数を呼び出すことで行われます。

# 例

```julia
julia> har_forecast_plot(figen(100,0.2), 10)
```
