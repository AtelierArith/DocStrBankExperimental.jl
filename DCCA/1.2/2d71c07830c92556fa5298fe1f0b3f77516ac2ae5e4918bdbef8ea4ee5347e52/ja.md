```
rhoDCCA(x,y; box_start = 3, box_stop = div(length(x),10), nb_pts = 30)
```

`x` と `y` の DCCA 分析を実行します。デフォルトの分析は、統計的理由から、ウィンドウサイズ 3 から `x` の全長の 10 分の 1 まで始まります。分析に使用される異なるウィンドウサイズと関連する dcca 係数を返します。
