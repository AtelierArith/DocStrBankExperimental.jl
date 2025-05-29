```
sparse_group_lasso(m::Chain, α=1)
```

スパース入力正則化のためのスパースグループラッソ項を取得します。これは、各入力特徴に対応する第一層ニューラルネットワークの重みのL1およびL2ノルムの組み合わせです。

参考文献: Feng & Simon, Sparse-Input Neural Networks for High-dimensional Nonparametric Regression and Classification, 2017 (pg. 4)。

**引数:**

  * `m`: ニューラルネットワークモデル
  * `α`: （オプション）ラッソ（`α=0`）対グループラッソ（`α=1`）のバランスパラメータ {0:1}

**戻り値:**

  * `w_norm`: スパースグループラッソ項
