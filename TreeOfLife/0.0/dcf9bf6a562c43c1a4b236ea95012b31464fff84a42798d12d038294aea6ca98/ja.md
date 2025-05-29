```
getage(tree::ChronoTree; 
	average=mean_, getrelerr::Bool=false, reltol=1e-6) :: Float64
```

木のティップノードの平均年齢（根ノードから）を返します。

引数 `average` は年齢を1つに要約する方法を定義します。デフォルトでは `mean_` に設定されています。

引数 `getrelerr` は、出力に相対標準偏差を追加するかどうかを制御します（`(mean, relstd)`）またはしないか（`mean` のみ）。デフォルトでは `false` に設定されています。

引数 `reltol` は相対誤差の許容範囲です。デフォルトでは `1e-6` に設定されています。判断を抑制するには、`reltol=NaN` に設定します。
