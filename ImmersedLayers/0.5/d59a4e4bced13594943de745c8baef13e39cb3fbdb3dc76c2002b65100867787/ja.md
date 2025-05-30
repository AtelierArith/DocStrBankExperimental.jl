```
Laplacian(cache::BasicILMCache,coeff_factor::Real[,with_inverse=true])
```

`cache`に関連付けられたインデックスまたはグリッドスケーリングを使用して、`cache`内のグリッド用の可逆ラプラス演算子を作成します。演算子は係数因子`coeff_factor`で事前に乗算されています。
