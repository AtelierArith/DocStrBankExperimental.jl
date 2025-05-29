```
extremevaltheory_gpdfit_pvalues(X, p; kw...)
```

さまざまな計算された量を返し、[`extremevaltheory_dims_persistences`](@ref)`(X, p; kw...)`の結果の重要性を定量化する方法を示します。これは、一般化パレート分布（GPD）が入力データの超過をどれだけよく説明するかを定量化するものです。

## キーワード引数

  * `show_progress = true`: 進行状況バーを表示します。
  * `TestType = ApproximateOneSampleKSTest`: 使用するテストタイプ。`ApproximateOneSampleKSTest, ExactOneSampleKSTest, CramerVonMises`のいずれかです。`OneSampleADTest`は時々意味のない結果をもたらすことがあることに注意しました：すべてのp値が等しく、非常に小さい値（≈ 1e-6）でした。
  * `nbins = round(Int, length(X)*(1-p)/20)`: NRMSEを計算するための超過のヒストグラムを計算する際に使用するビンの数。デフォルト値は、超過の長さを20で割った値に等しい等間隔のビンを使用します。

## 説明

この関数は、[`extremevaltheory_dims_persistences`](@ref)と同様に、各点$x_i \in X$に対して超過$E_i$を計算します。返されるのは5つの量で、すべて`length(X)`の長さのベクトルです：

  * `Es`、すべての超過、ベクトルのベクトルとして。
  * `sigmas, xis`、各超過に対するGPDフィットの適合したσ、ξ
  * `nrmses`、超過のヒストグラムに対するフィットしたGPDの正規化された二乗平均平方根距離
  * `pvalues`、GPDフィットの適切性に関する統計テストのp値

出力`nrmses`は、フィットしたGPDと超過の経験的ヒストグラムとの距離を定量化します。これは次のように計算されます。

$$
NRMSE = \sqrt{\frac{\sum{(P_j - G_j)^2}{\sum{(P_j - U)^2}}
$$

ここで、$P_j$はビン$j$での経験的（観測された）確率、$G_j$はビン$j$の中点でのフィットしたGPD確率、$U$は$G_j$と同じですが、均一分布のためのものです。式の分母は表現を正規化し、経験的分布の誤差が均一分布でフィッティングした経験的分布の誤差に正規化されるようにします。NRMSE < 1が期待されます。小さいほど、データがGPDによって均一分布よりもよく近似されていることを示します。

出力`pvalues`はp値のベクトルです。`pvalues[i]`は仮説*「点`X[i]`の周りの超過はGPDからサンプリングされている」*に対するp値に対応し、対立仮説はそれらがそうでないことです。p値を抽出するために、HypothesisTests.jlを使用してフィットしたGPDに対して一標本仮説を実行します。非常に小さいp値は、仮説を棄却すべきであり、データがGPDによってうまく説明されていないことを示します。これは、データが不十分であるか、量子確率`p`が高すぎるか、データが一般的に適していないことを示す可能性があります。このp値に基づく重要性の方法は、[^Faranda2017]で使用されていますが、正確にどのように使用されたかは不明です。

これらの量がどのように重要性を定量化するかの詳細については、私たちのレビュー論文を参照してください。

[^Faranda2017]: Faranda et al. (2017), Dynamical proxies of North Atlantic predictability and extremes, [Scientific Reports, 7](https://doi.org/10.1038/srep41278)
