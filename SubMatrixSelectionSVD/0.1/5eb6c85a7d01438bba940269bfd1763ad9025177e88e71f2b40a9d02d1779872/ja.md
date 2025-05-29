```
smssvd(X, d, stdThresholds=10 .^ range(-2,stop=0,length=100); nbrIter=10, maxSignalDim=typemax(Int)) -> (U,Σ,V,ps,signalDimensions,selectedVariables)
```

行列 X の部分行列選択特異値分解 (SMSSVD) を計算します。

**入力**

  * `X`: PxN データ行列 (P 変数と N サンプル)。
  * `d`: 結果の次元数。
  * `stdThresholds`: 投影スコアが評価される標準偏差フィルタリング閾値。X の変数の最大標準偏差の割合として表現されます。0 から 1 の間の増加する値のベクトルである必要があります。

**出力**

  * `U`: 左特異ベクトルの Pxd 行列 (変数の表現)。
  * `S`: 特異値の d ベクトル。
  * `V`: 右特異ベクトルの Nxd 行列 (サンプルの表現)。
  * `ps`: すべての投影スコアを持つ d x length(stdThresholds) 行列。プロットに便利です。
  * `signalDimensions`: SMSSVD によって検出された各信号の次元数を持つベクトル。
  * `selectedVariables`: 各信号について、投影スコアによって選択された変数を示すビットマスク。
