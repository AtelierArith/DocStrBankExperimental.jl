```
 interp2d(bd::BATS, var::AbstractString, plotrange=[-Inf, Inf, -Inf, Inf],
	 plotinterval=Inf; kwargs...)
```

データ `var` の2D補間スライスを `bd` から返します。`plotrange` が設定されていない場合、出力データの解像度は元のものと同じです。

# キーワード引数

  * `innermask=false`: 内部境界をNaNでマスクするかどうか。
  * `rbody=1.0`: 内部マスクの半径。ヘッダーにrbodyパラメータが見つからない場合に使用されます。
  * `useMatplotlib=true`: 散発的な補間にMatplotlib（高速）またはNaturalNeighboursを使用するかどうか。trueの場合、構築された三角形メッシュ上で線形補間が行われます。
