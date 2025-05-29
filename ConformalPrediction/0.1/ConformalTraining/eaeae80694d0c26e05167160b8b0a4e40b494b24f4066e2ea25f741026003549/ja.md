```
soft_assignment(conf_model::ConformalProbabilisticSet; temp::Real=0.1)
```

各ラベルとサンプルに対するソフトアサインメントスコアを計算します。つまり、ラベル `k` が信頼セットに含まれる確率です。この実装は Stutz et al. (2022) に従っています: https://openreview.net/pdf?id=t8O-4LKFVx。論文とは異なり、適合スコアの代わりに非適合スコアを使用するため、符号が反転しています。
