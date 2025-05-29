```
SeisDifference(d1, d2; <キーワード引数>)
```

時間-空間、2D地震データ `d1`、`d2`、およびその差 (`d1 - d2`) を色、ウィグル、またはオーバーレイでプロットします。プロットはデフォルトで水平に配置されます。

# 引数:

  * `d1::Matrix{<:AbstractFloat}`: 測定された地震トレース。列の数はトレースの数に対応し、行の数は各トレースの振幅が測定された回数に対応します。
  * `d2::Matrix{<:AbstractFloat}`: d1と同じ説明。

# キーワード引数:

  * `fig=nothing`: プロットしたい図。指定されていない場合は、新しい図が作成されて返されます。
  * `gx::Vector{<:Real}=nothing`: トレースに対応する地震計の実座標。
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
  * `cmap=:viridis`: 色とオーバーレイプロットに使用されるカラーマップ。
  * `style`: プロットの種類を決定します。"wiggle"/"wiggles"、"color"、"overlay"のいずれか。
  * `horizontal=true`: falseに設定すると、d1、d2、およびその差が垂直に配置されます。

図とd1、d2、d1-d2に対応する3つの軸を返します。

# 例

```julia
julia> d1 = SeisLinearEvents(); d2 = SeisLinearEvents();
julia> f, ax1, ax2, ax_diff = SeisDifference(d1, d2);
```

著者: Firas Al Chalabi (2024)
