```
lwplsr(; kwargs...)
lwplsr(X, Y; kwargs...)
```

k-最近傍法による局所加重部分最小二乗回帰 (kNN-LWPLSR)。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。

キーワード引数:

  * `nlvdis` : 類似性を計算する前に次元削減に使用するグローバルPLSで考慮する潜在変数 (LV) の数。`nlvdis = 0` の場合、次元削減は行われません。
  * `metric` : 隣接点を選択し、重みを計算するために使用される類似性のタイプ (関数 `getknn` を参照)。可能な値は: `:eucl` (ユークリッド)、`:mah` (マハラノビス)、`:sam` (スペクトル角距離)、`:cor` (相関距離)。
  * `h` : 関数 `winvs` によって計算される重み関数の形状を定義するスカラー。hが小さいほど、関数は鋭くなります。詳細については関数 `winvs` を参照してください（`winvs` のキーワード引数 `criw` と `squared` もここで指定できます）。
  * `k` : 各観測値を予測するために選択する最近傍の数。
  * `tolw` : 非常に近い隣接点の際の安定化のため。
  * `nlv` : ローカル (すなわち各近傍内) モデルの潜在変数 (LV) の数。
  * `scal` : ブール値。`true` の場合、(a) グローバル `X` の各列 (および事前にPLS次元削減がある場合のグローバル `Y`) は、距離と重みを計算する前にその未修正の標準偏差でスケーリングされ、(b) XとYのスケーリングも各近傍内 (ローカルレベル) で加重PLSRのために行われます。
  * `verbose` : ブール値。`true` の場合、予測情報が印刷されます。

関数 `lwplsr` は、Lesnoff et al. 2020 のような kNN-LWPLSR モデルをフィットさせます。パイプラインの一般的な原則は次のとおりです（多くの他のパイプラインのバリエーションを構築できます）：

LWPLSR は加重PLSR (WPLSR) の特別なケースです (例: Schaal et al. 2002)。WPLSR では、通常の 1/n (標準PLSR) とは異なる事前重みが n のトレーニング観測値に与えられます。これらの重みは、(i) WPLS のスコアとローディングを計算し、(ii) WPLS スコアに対して Y 応答をフィットさせる回帰モデルを計算するために使用されます。LWPLSR の特異性 (WPLSR と比較して) は、重みが予測する新しい観測値とトレーニング観測値との間の類似性 (例: 距離) から計算されることです ("L" は "localized" に由来します)。LWPLSR では、重み、したがってフィットした WPLSR モデルは、予測する新しい観測値ごとに変化します（「ユニーク」なフィットモデルは存在しません）。

元の LWPLSR では、各予測観測値に対してすべての n のトレーニング観測値が使用されます (例: Sicard & Sabatier 2006, Kim et al 2011)。n が大きい場合、これは非常に時間がかかる可能性があります。より速く (しばしばより効率的な) 戦略は、トレーニングセット内で予測する観測値に最も近い `k` の最近傍を事前に選択し ("重み付け 1")、その後この事前選択された近傍に対してのみ LWPLSR を適用することです ("重み付け 2")。この戦略は、関数 `lwplsr` に実装された kNN-LWPLSR に対応します。

`lwplsr` では、重み付け 1 と 2 に使用される類似性は、生の X データから直接計算されるか、引数 `nlvdis` に応じて次元削減の後に計算されます。最後の場合、グローバル PLS2 スコア (LV) は {`X`, `Y`} から計算され、類似性はこれらのスコアに対して計算されます。

一般に、高次元の X データに対しては、マハラノビス距離を使用するにはデータの事前次元削減が必要です。

## 参考文献

Kim, S., Kano, M., Nakagawa, H., Hasebe, S., 2011. 局所加重部分最小二乗法と統計的波長選択を用いた活性医薬品成分含量の推定。Int. J. Pharm., 421, 269-274.

Lesnoff, M., Metz, M., Roger, J.-M., 2020. 農業NIRデータにおける回帰と識別のための局所加重PLS戦略の比較。Journal of Chemometrics, e3209. https://doi.org/10.1002/cem.3209

Schaal, S., Atkeson, C., Vijayamakumar, S. 2002. リアルタイムロボット学習のための非パラメトリック統計からのスケーラブルな技術。Applied Intell., 17, 49-60.

Sicard, E. Sabatier, R., 2006. 局所PLS1回帰の理論的枠組みと降雨データセットへの適用。Comput. Stat. Data Anal., 51, 1393-1410.

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/cassav.jld2") 
@load db dat
@names dat
X = dat.X 
y = dat.Y.tbc
year = dat.Y.year
tab(year)
s = year .<= 2012
Xtrain = X[s, :]
ytrain = y[s]
Xtest = rmrow(X, s)
ytest = rmrow(y, s)

nlvdis = 15 ; metric = :mah 
h = 1 ; k = 500 ; nlv = 10
model = lwplsr(; nlvdis, metric, h, k, nlv) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm

res = predict(model, Xtest) ; 
@names res 
res.listnn
res.listd
res.listw
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction",  
    ylabel = "Observed").f    
```
