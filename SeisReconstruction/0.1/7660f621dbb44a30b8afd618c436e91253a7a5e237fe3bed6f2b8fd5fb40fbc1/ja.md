```
power_method(x0,Hop,PARAM)
```

POWER_METHOD: パワー反復法は、H'Hの最大固有値を計算します。ここで、HとH'はHopによって与えられます。この関数は、FISTAのステップパラメータを評価するために必要です。

# 引数

  * `x0`: H'*H*x0が中断しないような次元の初期シード
  * `Hop`: HとH'をカプセル化する線形演算子で、Hop(x,PARAM, 1) = H x および Hop(y,PARAM,-1) = H'y
  * `PARAM`: Hopとその随伴を実行するためのパラメータ
