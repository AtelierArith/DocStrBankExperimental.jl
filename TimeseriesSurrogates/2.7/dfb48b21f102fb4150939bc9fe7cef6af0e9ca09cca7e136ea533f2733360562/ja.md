```
surroplot(x, s; kwargs...) → fig
surroplot(x, method::Surrogate; kwargs...) → fig
surroplot!(fig_or_gridlayout, x, method::Surrogate)
```

時系列 `x` とそのサロゲート実現 `s` をプロットし、2つの時系列のパワースペクトルとヒストグラムを比較します。サロゲートを生成するためのメソッドが与えられた場合、`x` からサロゲートを作成し、それをプロットします。

## キーワード引数

  * `cx` と `cs`: 元の時系列とサロゲート時系列の色。
  * `nbins`: ヒストグラムのビンの数。
  * `kwargs...`: `Makie.Figure` に伝播される。
  * `resolution`: 図の解像度を指定するタプル。
