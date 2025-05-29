```
FDKplan{C,I,H,V}
```

FDKプランを格納するための構造体タイプ。

`view_weight` には（製品の）以下が含まれる場合があります。

  * 短いスキャン用のパーカー重み付け
  * `fdk_weight_cyl` からのビューごとのCBCT重み付け
  * `_angle_weights` からの非一様な角度の可能性がある `dβ` 重み付け
