```
SeisPlotFK(d; <キーワード引数>)
```

周波数-波数2D地震データ `d` をプロットします。

# 引数

  * `d::Matrix{<:AbstractFloat}`: プロットする2Dデータ。

# キーワード引数:

  * `fig=nothing`: プロットする図。指定しない場合は、新しい図が作成されて返されます。
  * `pclip=99.9`: クリップを決定するためのパーセンタイル。
  * `vmin=nothing`: カラーマッピングデータに使用される最小値。
  * `vmax=nothing`: カラーマッピングデータに使用される最大値。
  * `fmax=100`: `"FK"` または `"Amplitude"` プロットの最大周波数。
  * `dx=1`: x軸の増分。
  * `dy=1`: y軸の増分。
  * `cmap=:PuOr`: カラーマップ

dに対応する図と軸を返します。

# 例

```julia
julia> d = SeisLinearEvents();
julia> f, ax = SeisPlotFK(d);
```

著者: Firas Al Chalabi (2024) ```
