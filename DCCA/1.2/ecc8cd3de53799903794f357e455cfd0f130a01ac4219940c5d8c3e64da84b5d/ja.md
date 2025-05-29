```
dcca(x,y; box_start = 3, box_stop = div(length(x),10), nb_pts = 30)
```

`x`と`y`のDCCA分析を実行します。デフォルトの分析は、統計的理由から、ウィンドウサイズ3から`x`の全長の10分の1まで始まります。

dcca係数を返します。
