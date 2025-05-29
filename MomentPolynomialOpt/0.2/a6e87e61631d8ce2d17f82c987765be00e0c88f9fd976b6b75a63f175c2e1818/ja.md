```
K,I,P,B = annihilator(sigma::Series{R}, L, eqzero = is_zero)
```

正の系列 $σ$ の消去子のグレーデッド基底を、単項式のリスト L によって張られる空間で計算します。

出力は次のとおりです：

  * K グレーデッド基底
  * I K の初期単項式
  * P 直交基底
  * B 単項基底
