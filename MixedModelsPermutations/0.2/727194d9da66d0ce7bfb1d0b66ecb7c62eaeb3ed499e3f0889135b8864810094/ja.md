```
permutation([rng::AbstractRNG,] nsamp::Integer, m::LinearMixedModel;
            use_threads::Bool=false,
            β=zeros(length(coef(morig))),
            residual_permutation=:signflip,
            blup_method=ranef,
            residual_method=residuals)
```

`m`の`nsamp`個の非パラメトリックブートストラップ複製フィットを実行し、`MixedModelBootstrap`を返します。

デフォルトの乱数生成器は`Random.GLOBAL_RNG`です。

`GeneralizedLinearMixedModel`は現在サポートされていません。

# 名前付き引数

`progress=false`を使用してプログレスバーを無効にすることができます。プログレスバーは、非対話型（つまり、ログ記録）コンテキストでは自動的に無効になります。

残差のレベルでの置換は、符号反転（`residual_permutation=:signflip`）または古典的な置換/シャッフル（`residual_permutation=:shuffle`）のいずれかを介して実行できます。

`blup_method`は、どのように/どのグループレベルの効果が置換のために渡されるかのオプションを提供します。デフォルトの`ranef`は、縮小された条件付きモード/BLUPを使用します。通常の最小二乗法（OLS）からの縮小されていない推定値は`olsranef`で使用できます。このアプローチではグループレベルの推定値に縮小がないため、特異な推定値を回避できます。ただし、ランダム効果の設計行列がランク不足の場合（例：`MixedModels.fulldummy`の使用やデータ内の欠損セルによる）、この方法は失敗します。詳細については[`olsranef`](@ref)および`MixedModels.ranef`を参照してください。

`residual_method`は、観測レベルの残差が置換のためにどのように渡されるかのオプションを提供します。これは、モデルとBLUP（`blup_method`で計算されたもの）を引数として取る二引数関数である必要があります。`blup_method`で計算されたBLUPを無視したい場合でも、第二引数は必要ですが、関数内で単に使用しないことができます。

`inflation_method`は、[`permute!`](@ref)に渡されるインフレーション係数を計算するための三引数関数（モデル、`blup_method`で計算されたBLUP、`residual_method`で計算された残差）です。

一般に、置換は特定の（帰無）仮説をテストするために使用されます。この仮説は、`β`引数を設定して仮説に一致させることによって指定されます。たとえば、最初の係数がゼロであるという帰無仮説は次のように表現されます。

```julialang
julia> hypothesis = coef(model);
julia> hypothesis[1] = 0.0;
```

!!! note
    置換（テスト）はH0からのサンプルを生成し、そこからp値を計算することが可能です。ブートストラップは通常、H1からのサンプルを生成し、カバレッジ/信頼区間を生成するのに便利です。もちろん、信頼区間とp値は互いに双対であるため、一方から他方に変換することが可能です。


# 方法

ここで実装されている方法は、次のアプローチに基づいています。

ter Braak C.J.F. (1992) Permutation Versus Bootstrap Significance Tests in Multiple Regression and Anova. In: Jöckel KH., Rothe G., Sendler W. (eds) Bootstrapping and Related Techniques. Lecture Notes in Economics and Mathematical Systems, vol 376. Springer, Berlin, Heidelberg. https://doi.org/10.1007/978-3-642-48850-4_10

および

Winkler, A. M., Ridgway, G. R., Webster, M. A., Smith, S. M., & Nichols, T. E. (2014). Permutation inference for the general linear model. NeuroImage, 92, 381–397. https://doi.org/10.1016/j.neuroimage.2014.01.060

!!! warning
    この方法は、ゼロの符号反転が効果的なランダム化技術ではないため、特異なモデルに対して深刻な制限があります。


```
