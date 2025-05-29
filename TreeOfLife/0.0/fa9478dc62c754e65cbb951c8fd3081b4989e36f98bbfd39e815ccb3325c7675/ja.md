```
getages(tree::ChronoTree; average=mean_, reltol=1e-6) :: Vector{Float64}
```

木のすべてのノードの年齢（根ノードからの）を返します。

引数 `average` は年齢を1つに要約する方法を定義します。デフォルトでは `mean_` に設定されています。

引数 `reltol` は相対誤差の許容範囲です。デフォルトでは `1e-6` に設定されています。判断を抑制するには、`reltol=NaN` に設定します。
