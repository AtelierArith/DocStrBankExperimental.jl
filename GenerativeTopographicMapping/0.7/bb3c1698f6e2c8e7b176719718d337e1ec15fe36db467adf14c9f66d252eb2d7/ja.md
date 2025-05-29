```
GTM
```

GTMを構築するためのモデルタイプで、[GenerativeTopographicMapping.jl](https://github.com/john-waczak/GenerativeTopographicMapping.jl)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
GTM = @load GTM pkg=GenerativeTopographicMapping
```

`model = GTM()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`GTM(k=...)`のようにキーワード引数を提供します。

GenerativeTopographicMappingは、[Generative Topographic Mapping](https://direct.mit.edu/neco/article/10/1/215-234/6127)を実装しています。Neural Computation; Bishop, C.; (1998): "GTM: The Generative Topographic Mapping"

# トレーニングデータ

MLJまたはMLJBaseでは、`mach = machine(model, X)`を使用してデータにインスタンス`model`をバインドします。ここで、

  * `X`: 列がscitype `Continuous`の入力特徴の`Table`です。

`fit!(mach, rows=...)`でマシンをトレーニングします。

# ハイパーパラメータ

  * `k=16`: GTM潜在グリッドの一辺に沿ったノードの数。合計ノード数は`k²`です。
  * `m=4`: 合計RBFの数は`m²`です。
  * `s=2.0`: RBF分散のスケールファクター。
  * `α=0.1`: モデルの重み正則化パラメータ（正則化なしの場合は0.0）
  * `topology=:square`: 潜在空間のトポロジー。`:square`、`:cylinder`、または`:torus`のいずれか。
  * `tol=0.1`: 期待値最大化フィッティング中の収束を決定するために使用される許容誤差。
  * `nepochs=100`: 最大トレーニングエポック数。
  * `nrepeats=4`: GTMが収束したと見なされる前に`tol`以下で繰り返すステップの数。
  * `rand_init=false`: 重み行列`W`をランダムに初期化するかどうか。falseの場合、`W`はデータセットの最初の2つの主成分を使用して初期化されます。

# 操作

  * `transform(mach, X)`: 潜在ノード責任分布の平均に対応する座標`ξ₁`と`ξ₂`を返します。
  * `predict(mach, X)`: 潜在ノード責任分布のモードに対応するノードのインデックスを返します。

# フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `gtm`: `GTM`モデルによってフィットされた`GenerativeTopographicMap`オブジェクト。ノード座標、RBF平均、RBF分散、重みなどを含みます。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `W`: フィットされたGTM重み行列
  * `β⁻¹`: フィットされたGTM分散
  * `Φ`: ノードRBF活性化行列
  * `Ξ`: 潜在空間におけるノード座標
  * `Ψ`: データ空間における投影されたノード平均
  * `llhs`: トレーニングループの各イテレーションからの対数尤度値
  * `converged`: 収束基準が`niter`に達する前に満たされた場合は`true`
  * `AIC`: 赤池情報量基準
  * `BIC`: ベイズ情報量基準

# 例

```
using MLJ
gtm = @load GTM pkg=GenerativeTopographicMapping
model = gtm()
X, y = make_blob(100, 10; centers=5) # 合成データ
mach = machine(model, X) |> fit!
X̃ = transform(mach, X)

rpt = report(mach)
classes = rpt.classes
```
