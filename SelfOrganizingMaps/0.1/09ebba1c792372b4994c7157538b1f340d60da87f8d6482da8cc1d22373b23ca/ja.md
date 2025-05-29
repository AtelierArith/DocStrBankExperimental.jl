```
SelfOrganizingMap
```

自己組織化マップを構築するためのモデルタイプで、[SelfOrganizingMaps.jl](https://github.com/john-waczak/SelfOrganizingMaps.jl)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
SelfOrganizingMap = @load SelfOrganizingMap pkg=SelfOrganizingMaps
```

`model = SelfOrganizingMap()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`SelfOrganizingMap(k=...)`のようにキーワード引数を提供します。

SelfOrganizingMapsは、[コホーネンの自己組織化マップ](https://ieeexplore.ieee.org/abstract/document/58325?casa_token=pGue0TD38nAAAAAA:kWFkvMJQKgYOTJjJx-_bRx8n_tnWEpau2QeoJ1gJt0IsywAuvkXYc0o5ezdc2mXfCzoEZUQXSQ)、IEEEの議事録; Kohonen, T.; (1990): "自己組織化マップ"を実装しています。

# トレーニングデータ

MLJまたはMLJBaseでは、インスタンス`model`をデータにバインドします。`mach = machine(model, X)`の形式で、ここで

  * `X`: 列がscitype `Continuous`の入力特徴の`AbstractMatrix`または`Table`です。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `k=10`: SOMグリッドの一辺に沿ったノードの数。合計ノード数は`k²`です。
  * `η=0.5`: 学習率。トレーニングの各ラウンド中に勝利ノードとその隣接ノードに対して行われる調整のスケール。
  * `σ²=0.05`: （二乗）隣接半径。隣接ノードの調整のスケールを決定するために使用されます。
  * `grid_type=:rectangular`  ノードグリッドの幾何学。`(:rectangular, :hexagonal, :spherical)`のいずれか。
  * `η_decay=:exponential` 学習率スケジュール関数。`(:exponential, :asymptotic)`のいずれか。
  * `σ_decay=:exponential` 隣接半径スケジュール関数。`(:exponential, :asymptotic, :none)`のいずれか。
  * `neighbor_function=:gaussian` 隣接重みの調整に使用されるカーネル関数。スケールは`σ²`によって設定されます。`(:gaussian, :mexican_hat)`のいずれか。
  * `matching_distance=euclidean` 勝利ノードを決定するために使用される`Distances.jl`の距離関数。
  * `Nepochs=1` シャッフルされたデータセットでトレーニングを繰り返す回数。

# 操作

  * `transform(mach, Xnew)`: `Xnew`の各インスタンスに対する勝利SOMノードの座標を返します。グリッドタイプが`:rectangular`および`:hexagonal`の場合、これらはデカルト座標です。グリッドタイプが`:spherical`の場合、これらはラジアンでの緯度と経度です。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `coords`: SOMノードの各座標（マップのドメイン内のポイント）で、形状は(k², 2)です。
  * `weights`: SOMノードの重みベクトルの配列（マップの範囲内の対応するポイント）で、形状は(k², 入力次元)です。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `classes`: トレーニングデータXの各インスタンスに対する勝利ノードのインデックスで、クラスラベルとして解釈されます。

# 例

```
using MLJ
som = @load SelfOrganizingMap pkg=SelfOrganizingMaps
model = som()
X, y = make_regression(50, 3) # 合成データ
mach = machine(model, X) |> fit!
X̃ = transform(mach, X)

rpt = report(mach)
classes = rpt.classes
```
