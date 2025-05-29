```
RobustVCE(nparam::Integer, nmoment::Integer, nobs::Integer; kwargs...)
```

ヘテロスケダスティシティにロバストな分散共分散推定器の仕様とキャッシュのためのオブジェクトを構築します。関連するGMM問題は、`nparam` パラメータ、`nmoment` モーメント条件、および `nobs` サンプル観測を含みます。

# キーワード

  * `adjustdofr::Integer=0`: 残差自由度の有限サンプル調整。
  * `TF::Type=Float64`: 数値値の型。
