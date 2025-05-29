```
make_yaxis(fig,ang::Number,max::Number,label::String,ticks::Tuple)
```

y軸がx軸に対して<90°の角度を持つように、ゼロから軸をプロットします。

# 入力

  * `fig` : 実際の図
  * `ang` : y軸とx軸の間の角度（ラジアン）
  * `max` : 軸の最大値
  * `label` : 軸のラベル
  * `ticks` : 軸の目盛り（タプルの形式 : (ticks, tickslabels)）
