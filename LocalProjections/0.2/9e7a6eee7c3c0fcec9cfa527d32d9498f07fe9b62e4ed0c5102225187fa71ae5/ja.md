```
HARVCE{LR<:LongRunVariance} <: CovarianceEstimator
```

長期分散推定量 `LR` の型を持つヘテロスケダスティシティ-自己相関-ロバスト分散-共分散推定器。

# フィールド

  * `lr::LR`: 長期分散推定器。
  * `bw::Function`: サンプル内の期間数の関数としてのバンド幅。
  * `cv::Function`: テストのレベルとバンド幅の関数としての臨界値。
  * `pv::Function`: テスト統計量とバンド幅の関数としてのp値。
