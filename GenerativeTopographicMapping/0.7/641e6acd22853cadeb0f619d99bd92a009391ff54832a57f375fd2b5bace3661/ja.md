```
GSMLinear
```

GSM線形を構築するためのモデルタイプで、[GenerativeTopographicMapping.jl](https://github.com/john-waczak/GenerativeTopographicMapping.jl)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
GSMLinear = @load GSMLinear pkg=GenerativeTopographicMapping
```

`model = GSMLinear()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`GSMLinear(k=...)`のようにキーワード引数を提供します。

生成的単純形マッピングは、[Generative Topographic Mapping](https://direct.mit.edu/neco/article/10/1/215-234/6127)に基づいており、Neural Computation; Bishop, C.; (1998): "GTM: The Generative Topographic Mapping"では、潜在点がグリッド化されたn-単純形として構成されています。

# トレーニングデータ

MLJまたはMLJBaseでは、`model`のインスタンスをデータにバインドします。`mach = machine(model, X)`の形式で、ここで

  * `X`: 列がscitype `Continuous`の入力特徴の`Table`です。

`fit!(mach, rows=...)`でマシンをトレーニングします。

# ハイパーパラメータ

  * `k=10`: 潜在空間単純形グリッドのエッジごとの潜在ノードの数。
  * `Nv=3`: 単純形の頂点の数、すなわちエンドメンバーの数。
  * `λ=0.1`: モデル重みの正則化パラメータ。
  * `make_positive=false`:
  * `nepochs=100`: 最大トレーニングエポック数。
  * `tol=0.1`: 期待値最大化フィッティング中の収束を決定するために使用される許容誤差。
  * `nconverged=4`: GSMLinearが収束したと見なされる前に`tol`以下で繰り返すステップの数。
  * `rng=123`: モデル重みの初期化に使用される乱数シードまたは乱数生成器。

# 操作

  * `transform(mach, X)`: 潜在ノードの責任分布の平均に対応する座標`ξᵢ`を返します。
  * `predict(mach, X)`: 潜在ノードの責任分布のモードに対応するノードのインデックスを返します。

# フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `gsm`: `GSMLinear`モデルによってフィットされた`GenerativeSimplexMap`オブジェクト。ノード座標、RBF平均、RBF分散、重みなどを含みます。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `W`: フィットされたGTM重み行列
  * `β⁻¹`: フィットされたGTM分散
  * `Φ`: ノードRBF活性化行列
  * `node_data_means`: データ空間における投影されたノード平均
  * `Z`: 潜在空間におけるノード座標
  * `Q`: EMルーチン中に最大化された目的関数
  * `llhs`: トレーニングループの各イテレーションからの対数尤度値
  * `converged`: 収束基準が`niter`に達する前に満たされた場合は`true`
  * `AIC`: 赤池情報量基準
  * `BIC`: ベイズ情報量基準

# 例

```
using MLJ
gsm = @load GSMLinear pkg=GenerativeTopographicMapping
model = gsm()
X, y = make_blob(100, 10; centers=5) # 合成データ
mach = machine(model, X) |> fit!
X̃ = transform(mach, X)

rpt = report(mach)
classes = rpt.classes
```
