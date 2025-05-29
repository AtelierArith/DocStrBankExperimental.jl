```
nonparametricbootstrap([rng::AbstractRNG,] nsamp::Integer, m::LinearMixedModel;
                       use_threads=false, blup_method=ranef, β=coef(morig))
```

`m`の`nsamp`非パラメトリックブートストラップ複製フィットを実行し、`MixedModelBootstrap`を返します。

デフォルトの乱数生成器は`Random.GLOBAL_RNG`です。

`GeneralizedLinearMixedModel`は現在サポートされていません。

# 名前付き引数

`progress=false`を使用して進捗バーを無効にすることができます。進捗バーは、非対話型（つまり、ログ記録）コンテキストでは自動的に無効になります。

`blup_method`は、再サンプリングのためにどのように/どのグループレベルの効果が渡されるかのオプションを提供します。デフォルトの`ranef`は、縮小された条件付きモード/BLUPを使用します。通常の最小二乗法（OLS）からの非縮小推定値は`olsranef`で使用できます。このアプローチではグループレベルの推定値の縮小は行われず、特異な推定値を回避できます。ただし、ランダム効果の設計行列がランク不足の場合（例：`MixedModels.fulldummy`の使用やデータの欠落セルによる）、この方法は失敗します。詳細については[`olsranef`](@ref)および`MixedModels.ranef`を参照してください。

`residual_method`は、観測レベルの残差が置換のためにどのように渡されるかのオプションを提供します。これは、モデルとBLUP（`blup_method`で計算されたもの）を引数として取る二引数関数である必要があります。`blup_method`で計算されたBLUPを無視したい場合でも、第二引数は必要ですが、関数内で単に使用しないことができます。

`inflation_method`は、[`resample!`](@ref)に渡されるインフレーションファクターを計算するための三引数関数（モデル、`blup_method`で計算されたBLUP、`residual_method`で計算された残差）です。

# メソッド

ここで実装されているメソッドは、次の文献のセクション3.2に示されたアプローチに基づいています: Carpenter, J.R., Goldstein, H. and Rasbash, J. (2003). A novel bootstrap procedure for assessing the relationship between class size and achievement. Journal of the Royal Statistical Society: Series C (Applied Statistics), 52: 431-443. https://doi.org/10.1111/1467-9876.00415 ```
