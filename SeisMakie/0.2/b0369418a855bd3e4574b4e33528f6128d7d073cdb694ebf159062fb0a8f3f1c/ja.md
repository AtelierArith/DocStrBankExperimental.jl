```
seiswiggleplot(d; <キーワード引数>)
seiswiggleplot!(ax, d; <キーワード引数>)
```

2D地震データ`d`の時間-空間のウィグルプロットを描画するためのレシピ。

# 引数:

  * `d::Matrix{<:AbstractFloat}`: 測定された地震トレース。列の数はトレースの数に対応し、行の数は各トレースの振幅が測定された回数に対応します。

# キーワード引数:

  * `gx::Vector{<:Real}=nothing`: dのトレースに対応する地震計の実座標。
  * `ox=0`: x軸の最初の点。
  * `dx=1`: x軸の増分。
  * `oy=0`: y軸の最初の点。
  * `dy=1`: y軸の増分。
  * `wiggle_fill_color=:black`: 正のウィグルを塗りつぶすための色。
  * `wiggle_line_color=:black`: ウィグルの線の色。
  * `wiggle_trace_increment=1`: ウィグルトレースの増分。
  * `xcur=1.2`: トレースのウィグルの振れ幅。

# 例

```julia
julia> d = SeisLinearEvents();
julia> f, ax, wp = seiswiggleplot(d)
```

```julia
julia> d = SeisLinearEvents(); f = Figure(); ax = Axis(f)
julia> wp = seiswiggleplot!(ax, d)
```

**注意: アニメーションは、このレシピでobservable `d`を同じサイズの行列で更新した場合にのみ機能します。**

著者: Firas Al Chalabi (2024) クレジット: Aaron Stanton (2015) 

  * このファイルのコードは、SeisPlot.jlのAaron Stantonのいくつかのコードに触発されています。
