```
seisimageplot(d; <キーワード引数>);
seisimageplot!(ax, d; <キーワード引数>);
```

2D地震データ`d`の時間-空間、カラープロットを描画するためのレシピ。

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
  * `cmap=:seismic`: 使用されるカラーマップ。

# 例

```julia
julia> d = SeisLinearEvents();
julia> f, ax, img = seisimageplot(d)
```

```julia
julia> d = SeisLinearEvents(); f = Figure(); ax = Axis(f)
julia> img = seisimageplot!(ax, d)
```

著者: Firas Al Chalabi (2024) クレジット: Aaron Stanton (2015)

  * このファイルのコードの大部分は、Aaron Stantonによって書かれたSeisPlot.jlから取られています。
