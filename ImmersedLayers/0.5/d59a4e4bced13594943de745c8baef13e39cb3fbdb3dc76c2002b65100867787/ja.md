```
Laplacian(cache::BasicILMCache,coeff_factor::Real[,with_inverse=true])
```

`cache`に関連付けられたインデックスまたはグリッドスケーリングを使用して、`cache`内のグリッド用の可逆ラプラシアン演算子を作成します。演算子は係数`coeff_factor`で事前に乗算されています。
