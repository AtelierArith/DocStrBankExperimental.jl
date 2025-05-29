```
seisoverlayplot(d; <キーワード引数>)
seisoverlayplot!(ax, d; <キーワード引数>)
```

2D地震データ`d`の時間-空間オーバーレイプロットを描画するためのレシピ。

# 引数:

  * `d::Matrix{<:AbstractFloat}`: プロットする2D地震データ。

# キーワード引数:

  * `ox=0`: x軸の最初の点。
  * `dx=1`: x軸の増分。
  * `oy=0`: y軸の最初の点。
  * `dy=1`: y軸の増分。
  * `pclip=98`: クリップを決定するためのパーセンタイル。
  * `vmin=nothing`: カラーマッピングデータに使用される最小値。
  * `vmax=nothing`: カラーマッピングデータに使用される最大値。
  * `wiggle_fill_color=:black`: 正のウィグルを塗りつぶすための色。
  * `wiggle_line_color=:black`: ウィグルの線の色。
  * `wiggle_trace_increment=1`: ウィグルトレースの増分。
  * `xcur=1.2`: クリップに対応するトレースのウィグルの振れ幅。
  * `cmap=:seismic`: 使用されるカラーマップ。

# 例

```julia
julia> d = SeisLinearEvents();
julia> f, ax, ov = seisoverlayplot(d)
```

```julia
julia> d = SeisLinearEvents(); f = Figure(); ax = Axis(f)
julia> ov = seisoverlayplot!(ax, d)
```
