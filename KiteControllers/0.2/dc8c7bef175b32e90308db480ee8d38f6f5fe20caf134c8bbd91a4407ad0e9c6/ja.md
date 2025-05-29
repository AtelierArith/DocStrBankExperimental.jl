```
function calc_steering(fpc, parking)
```

ステアリング出力 u*s と旋回率誤差 err を計算しますが、信号 Kpsi*out、Ku*out、int*in も計算します。

これは、次の図に示されている Simulink ブロックダイアグラムを実装します: 01*doc/flight*path*controller*I.png

パラメータ parking が true の場合、進行方向のみが制御され、コースは制御されません。
