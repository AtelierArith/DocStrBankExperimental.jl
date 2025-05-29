```
identify_cocos(sigma_B0, sigma_Ip, sigma_q, sigma_dpsi, clockwise_phi) -> COCOS IDのリスト
```

COCOS座標系を特定するためのユーティリティ関数です。複数のCOCOSが可能な場合は、すべてが返されます。

引数:

  * sigma_B0 - (+1,-1) トロイダル磁場の符号
  * sigma_Ip - (+1,-1) トロイダルプラズマ電流の符号
  * sigma_q  - (+1,-1) プラズマ内の安全係数 (q) の符号
  * sigma_dpsi -  +1 は psi が増加している場合、-1 は psi が減少している場合
  * clockwise_phi::Bool - (オプション) [true, false] phi角が時計回りに定義されているかどうか。これは奇数と偶数のCOCOSを特定するために必要です。この情報はコードの出力からは決定できないことに注意してください。
