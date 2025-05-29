```
phylolm(f::StatsModels.FormulaTerm, fr::AbstractDataFrame, net::HybridNetwork; kwargs...)
```

データに対して系統線形回帰モデルを適合させます。タイプ [`PhyloNetworkLinearModel`](@ref) のオブジェクトを返します。これは、`object.lm` に GLM パッケージからの線形モデルを含み、タイプは [GLM.LinearModel](https://juliastats.org/GLM.jl/stable/api/#GLM.LinearModel) です。

## 引数

  * `f`: 回帰に使用する式、[StatsModels](https://juliastats.org/StatsModels.jl/stable/) を参照してください。
  * `fr`: 応答値、予測値、各観測/行の種/ティップラベルを含む DataFrame。
  * `net`: 使用する系統ネットワーク。ラベル付きのティップを持っている必要があります。

キーワード引数

  * `model="BM"`: 特性進化のモデル（文字列として） "lambda"（Pagel のラムダ）、"scalinghybrid" は他の可能な値です（[`ContinuousTraitEM`](@ref) を参照）。
  * `tipnames=:tipnames`: 種/ティップラベルの列名、シンボルとして表されます。たとえば、`fr` にある種/ティップラベルを含む列が "Species" と名付けられている場合、`tipnames=:Species` とします。
  * `no_names=false`: `true` の場合、関数がティップ名を無視するよう強制します。この場合、データはネットワークのティップと同じ順序であると仮定されます。デフォルトは false で、true に設定することは危険であり、強く推奨されません。
  * `reml=true`: `true` の場合、分散成分の推定に REML 基準（"restricted maximum likelihood"）を使用し、そうでない場合は ML 基準を使用します。
  * `suppresswarnings=false`: `true` の場合、PhyloTraits 特有の警告が抑制されます。現在、Pagel のラムダモデルのみが警告を発生させる可能性があります（ネットワークが時間的一貫性を持たない場合）。

以下の許容パラメータは、`model="lambda"` または `model="scalinghybrid"` の場合にラムダの最適化を制御し、`model="BM"` かつ `withinspecies_var=true` の場合に分散成分の最適化を制御します。

  * `fTolRel=1e-10`: 尤度値に対する相対許容誤差
  * `fTolAbs=1e-10`: 尤度値に対する絶対許容誤差
  * `xTolRel=1e-10`: パラメータ値に対する相対許容誤差
  * `xTolAbs=1e-10`: パラメータ値に対する絶対許容誤差
  * `startingValue=0.5`: `model`="lambda" または "scalinghybrid" の場合、ラムダの最適化のための開始値を提供します。
  * `fixedValue=missing`: `model`="lambda" または "scalinghybrid" の場合、`fixedValue` が数値であれば、ラムダはこの数値に設定され、最適化されません。
  * `withinspecies_var=false`: `true` の場合、種内変動モデルを適合させます。現在、`model`="BM" のみで実装されています。
  * `y_mean_std::Bool=false`: `true` の場合、`withinspecies_var=true` であれば、種内変動を考慮し、`fr` に提供された種レベルの統計を使用します。

## 適合したモデルに適用されるメソッド

応答値にアクセスするには、`response(object)` を実行します。モデル行列にアクセスするには、`modelmatrix(object)` を実行します。モデル式にアクセスするには、`formula(object)` を実行します。

## 種内変動

高レベルの説明については、[`PhyloNetworkLinearModel`](@ref) を参照してください。応答変数における種内変動を持つモデルを適合させるには、データフレーム `fr` に次のいずれかを提供する必要があります：

(1) 個体レベルのデータ：応答、予測因子、種/ティップラベルの列が必要です。各行は個体の観測に対応する必要があります。少なくとも1つの種は2人以上の個体で表される必要があります。

(2) 種レベルの統計：平均応答、予測因子、種/ティップラベル、種サンプルサイズ（各種の個体数）、および種の標準偏差（種ごとの応答値の標準偏差）の列が必要です。各行は種に対応する必要があります：各種はユニークな行で表される必要があります。種サンプルサイズと種の標準偏差の列名は、"[応答列名]*n" および "[応答列名]*sd" であることが期待されます。たとえば、応答列名が "y" の場合、サンプルサイズと標準偏差の列名は "y*n" と "y*sd" になります。

データが（1）または（2）のいずれかに従うかどうかにかかわらず、`withinspecies_var` は true に設定する必要があります。データが（2）に従う場合、`y_mean_std` は false に設定する必要があります。

## 予測因子における種内変動

モデルは、予測因子における*種内変動がない*ことを前提としています。これは、予測因子と応答の間の進化的（歴史的、系統的）関係を捉えることを目的としており、種内（現在の、または表現型の）関係を捉えるものではありません。

個体レベルのデータに対して種内変動モデルが適合され、同じ種内の個体が同じ予測因子に対して異なる値を持つ場合、これらの値はすべてその種のすべての個体の平均予測因子値に置き換えられます。たとえば、ある種に3つの個体があり、それらの予測因子値が (x₁=3, x₂=6)、(x₁=4, x₂=8)、(x₁=2, x₂=1) であるとします。すると、これらの3つの個体の予測因子値は、モデル適合前に (x₁=(3+4+2)/3, x₂=(6+8+1)/3) に置き換えられます。もし4番目の個体がデータ (x₁=10, x₂=missing) を持っていた場合、その個体は x₂ を使用するモデルでは無視され、そのモデルの種データに対して情報を提供しません。

## 欠損データ

応答または予測因子のいずれかに欠損データがある行は、モデル適合から省かれます。応答、予測因子、種/ティップラベルの列が最小限必要です。上記のように、種内変動を適合させるためには追加の列が必要な場合があります。種名、種の標準偏差/サンプルサイズの列に欠損データがあるとエラーが発生します。

## 参照

[`rand`](@ref), [`ancestralreconstruction`](@ref), [`PhyloNetworks.vcv`](@extref)

## 例：種内変動なし

まず、パッケージからデータを読み込み、デフォルトの BM モデルを適合させます。

```jldoctest phylolmdoc
julia> phy = readnewick(joinpath(dirname(pathof(PhyloTraits)), "..", "examples", "caudata_tree.txt"));

julia> using DataFrames, CSV # データファイルを読み込むため、次に

julia> dat = CSV.read(joinpath(dirname(pathof(PhyloTraits)), "..", "examples", "caudata_trait.txt"), DataFrame);

julia> using StatsModels # 統計モデルの式のため

julia> fitBM = phylolm(@formula(trait ~ 1), dat, phy; reml=false);

julia> fitBM # 概要を表示
PhyloNetworkLinearModel

Formula: trait ~ 1

Model: Brownian motion

Parameter Estimates, using ML:
phylogenetic variance rate: 0.00294521

Coefficients:
─────────────────────────────────────────────────────────────────────
             Coef.  Std. Error      t  Pr(>|t|)  Lower 95%  Upper 95%
─────────────────────────────────────────────────────────────────────
(Intercept)  4.679    0.330627  14.15    <1e-31    4.02696    5.33104
─────────────────────────────────────────────────────────────────────
Log Likelihood: -78.9611507833
AIC: 161.9223015666
```

追加のパラメータ、尤度、AIC などを取得できます。

```jldoctest phylolmdoc
julia> round(sigma2_phylo(fitBM), digits=6) # jldoctest の便宜のために丸め
0.002945

julia> round(mu_phylo(fitBM), digits=4)
4.679

julia> using StatsBase # aic() stderror() loglikelihood() などのため

julia> round(loglikelihood(fitBM), digits=10)
-78.9611507833

julia> round(aic(fitBM), digits=10)
161.9223015666

julia> round(aicc(fitBM), digits=10)
161.9841572367

julia> round(bic(fitBM), digits=10)
168.4887090241

julia> round.(coef(fitBM), digits=4)
1-element Vector{Float64}:
 4.679

julia> confint(fitBM) # 係数の95%（デフォルト）信頼区間
1×2 Matrix{Float64}:
 4.02696  5.33104

julia> abs(round(r2(fitBM), digits=10)) # jldoctest の便宜のための絶対値
0.0

julia> abs(round(adjr2(fitBM), digits=10))
0.0

julia> round.(vcov(fitBM), digits=6) # 推定されたパラメータの分散共分散：二乗標準誤差
1×1 Matrix{Float64}:
 0.109314
```

残差は予測因子によって説明されない分散です。BM によってモデル化された系統的相関はそれらに関するものです。特性は、応答と関連する可能性のある予測因子から、また残差からの2つの系統信号の源を持つ可能性があります。

```jldoctest phylolmdoc
julia> round.(residuals(fitBM), digits=6)
197-element Vector{Float64}:
 -0.237648
 -0.357937
 -0.159387
 -0.691868
 -0.323977
 -0.270452
 -0.673486
 -0.584654
 -0.279882
 -0.302175
  ⋮
 -0.777026
 -0.385121
 -0.443444
 -0.327303
 -0.525953
 -0.673486
 -0.603158
 -0.211712
 -0.439833

julia> round.(response(fitBM), digits=5)
197-element Vector{Float64}:
 4.44135
 4.32106
 4.51961
 3.98713
 4.35502
 4.40855
 4.00551
 4.09434
 4.39912
 4.37682
 ⋮
 3.90197
 4.29388
 4.23555
 4.3517
 4.15305
 4.00551
 4.07584
 4.46729
 4.23917

julia> round.(predict(fitBM), digits=5)
197-element Vector{Float64}:
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 ⋮
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
```

## 例：種内変動あり（2つの異なる入力形式を示す）

ここでは小さなネットワークを使用します。データを個体ごとに1行、種ごとに複数行として入力できます。

```jldoctest phylolmdoc
julia> net = readnewick("((((D:0.4,C:0.4):4.8,((A:0.8,B:0.8):2.2)#H1:2.2::0.7):4.0,(#H1:0::0.3,E:3.0):6.2):2.0,O:11.2);");

julia> df = DataFrame( # 個体レベルの観測
           species = repeat(["D","C","A","B","E","O"],inner=3),
           trait1 = [4.08298,4.08298,4.08298,3.10782,3.10782,3.10782,2.17078,2.17078,2.17078,1.87333,1.87333,
              1.87333,2.8445,2.8445,2.8445,5.88204,5.88204,5.88204],
           trait2 = [-7.34186,-7.34186,-7.34186,-7.45085,-7.45085,-7.45085,-3.32538,-3.32538,-3.32538,-4.26472,
              -4.26472,-4.26472,-5.96857,-5.96857,-5.96857,-1.99388,-1.99388,-1.99388],
           trait3 = [18.8101,18.934,18.9438,17.0687,17.0639,17.0732,14.4818,14.1112,14.2817,13.0842,12.9562,
              12.9019,15.4373,15.4075,15.4317,24.2249,24.1449,24.1302]);

julia> m1 = phylolm(@formula(trait3 ~ trait1), df, net;
                    tipnames=:species, withinspecies_var=true)
PhyloNetworkLinearModel

Formula: trait3 ~ 1 + trait1

Model: Brownian motion

Parameter Estimates, using REML:
phylogenetic variance rate: 0.156188
within-species variance: 0.0086343

Coefficients:
──────────────────────────────────────────────────────────────────────
               Coef.  Std. Error     t  Pr(>|t|)  Lower 95%  Upper 95%
──────────────────────────────────────────────────────────────────────
(Intercept)  9.65347    1.3066    7.39    0.0018    6.02577   13.2812
trait1       2.30358    0.276163  8.34    0.0011    1.53683    3.07033
──────────────────────────────────────────────────────────────────────
Log Likelihood: 1.9446255188
AIC: 4.1107489623
```

あるいは、データを種ごとに1行、応答特性の個体間の標準偏差と、SD を計算した個体数の2つの追加列として入力できます。結果は同じです。

```jldoctest phylolmdoc
julia> df_r = DataFrame( # 種レベルの統計（サンプル平均、標準偏差）
           species = ["D","C","A","B","E","O"],
           trait1 = [4.08298,3.10782,2.17078,1.87333,2.8445,5.88204],
           trait2 = [-7.34186,-7.45085,-3.32538,-4.26472,-5.96857,-1.99388],
           trait3 = [18.896,17.0686,14.2916,12.9808,15.4255,24.1667],
           trait3_sd = [0.074524,0.00465081,0.185497,0.0936,0.0158379,0.0509643],
           trait3_n = [3, 3, 3, 3, 3, 3]);

julia> m2 = phylolm(@formula(trait3 ~ trait1), df_r, net;
                tipnames=:species, withinspecies_var=true, y_mean_std=true)
PhyloNetworkLinearModel

Formula: trait3 ~ 1 + trait1

Model: Brownian motion

Parameter Estimates, using REML:
phylogenetic variance rate: 0.15618
within-species variance: 0.0086343

Coefficients:
──────────────────────────────────────────────────────────────────────
               Coef.  Std. Error     t  Pr(>|t|)  Lower 95%  Upper 95%
──────────────────────────────────────────────────────────────────────
(Intercept)  9.65342    1.30657   7.39    0.0018    6.02582   13.281
trait1       2.30359    0.276156  8.34    0.0011    1.53686    3.07032
──────────────────────────────────────────────────────────────────────
Log Likelihood: 1.9447243714
AIC: 4.1105512573
```
