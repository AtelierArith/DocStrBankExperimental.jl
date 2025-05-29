```
seisamplitudeplot(d; <キーワード引数>)
seisamplitudeplot!(ax, d; <キーワード引数>)
```

振幅-周波数2D地震データ `d` をプロットします。

# 引数

  * `d::Array{Real,2}`: プロットする2Dデータ。

# キーワード引数

  * `fmax=100`: 最大周波数。
  * `dy=0.004`: 時間サンプル間隔。
  * `normalize=false`: データを正規化するかどうか。
  * `color=:black`: プロットの色。
  * `label=""`: 凡例に含めるプロットラベル。

# 例

```julia
julia> d = SeisLinearEvents();
julia> f, ax, amp = seisamplitudeplot(d)
```

```julia
julia> d = SeisLinearEvents(); f = Figure(); ax = Axis(f)
julia> amp = seisamplitudeplot!(ax, d)
```

著者: Firas Al Chalabi (2024) クレジット: Aaron Stanton (2015)

  * このファイルの大部分のコードは、Aaron Stantonによって書かれたSeisPlot.jlから取られています。
