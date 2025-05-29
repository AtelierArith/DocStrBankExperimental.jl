```
SeisPlotTX(d; <キーワード引数>)
```

時間-空間、2D地震データ `d` を画像、ウィグル、またはオーバーレイでプロットします。

# 引数:

  * `d::Matrix{<:AbstractFloat}`: 測定された地震トレース。列の数はトレースの数に対応し、行の数は各トレースの振幅が測定された回数に対応します。

# キーワード引数:

  * `fig=nothing`: プロットしたい図。指定されていない場合は、新しい図が作成されて返されます。
  * `gx::Vector{<:Real}=nothing`: `d` のトレースに対応する地震計の実際の座標。スタイル="wiggles" のみサポートされています。
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
  * `cmap=:seismic`: 画像およびオーバーレイプロットに使用されるカラーマップ。
  * `style`: プロットのタイプを決定します。"wiggle"/"wiggles"、"image"、"overlay" のいずれかです。

`d` に対応する図と軸を返します。

# 例

```julia
julia> d = SeisLinearEvents();
julia> f, ax = SeisPlotTX(d);
```

著者: Firas Al Chalabi (2024)
