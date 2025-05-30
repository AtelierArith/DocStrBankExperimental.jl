```
MDN
```

Mixture Density Networkを構築するためのモデルタイプで、[MixtureDensityNetworks.jl](https://github.com/JoshuaBillson/MixtureDensityNetworks.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
MDN = @load MDN pkg=MixtureDensityNetworks
```

`model = MDN()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`MDN(mixtures=...)`のようにキーワード引数を提供します。

ターゲット変数`y`に条件付けられたガウス混合モデル（GMM）をパラメータ化するニューラルネットワークです。

# トレーニングデータ

MLJまたはMLJBaseでは、`MDN`インスタンス`model`をデータにバインドします。`mach = machine(model, X, y)`の形式で行います。

  * `X`: `Continuous`スカイタイプに属する列を持つ任意の入力特徴のテーブル（例：`DataFrame`）。
  * `y`: 要素のスカイタイプが`Continuous`である任意の`AbstractVector`。

# ハイパーパラメータ

  * `mixtures=5`: 予測分布におけるガウス混合の数
  * `layers=[128,]`: 最初の隠れ層から始まる隠れ層のトポロジー
  * `η=1e-3`: オプティマイザに使用される学習率
  * `epochs=1`: モデルをトレーニングするエポックの数
  * `batchsize=32`: トレーニング中に使用されるバッチサイズ

# 操作

  * `predict(mach, Xnew)`: 新しい特徴`Xnew`に条件付けられたターゲットの分布を返します。`X`と同じスカイタイプを持つ必要があります。
  * `predict_mode(mach, Xnew)`: 新しい特徴`Xnew`に条件付けられたターゲットの分布の最大モードを返します。`X`と同じスカイタイプを持つ必要があります。
  * `predict_mean(mach, Xnew)`: 新しい特徴`Xnew`に条件付けられたターゲットの分布の平均を返します。`X`と同じスカイタイプを持つ必要があります。
  * `predict_median(mach, Xnew)`: 新しい特徴`Xnew`に条件付けられたターゲットの分布の中央値を返します。`X`と同じスカイタイプを持つ必要があります。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `fitresult`: Fluxエコシステムと互換性のあるトレーニングされた混合密度モデル。

# レポート

  * `learning_curve`: 各エポックの平均トレーニング損失。
  * `best_epoch`: 最も低いトレーニング損失を持つエポック（1から始まる）。
  * `best_loss`: トレーニング中に遭遇した最良（最低）損失。最良エポックの平均損失に対応します。

# アクセサ関数

  * `training_losses(mach)`は、各エポックの平均トレーニング損失のベクトルとして学習曲線を返します。

# 例

```
using MLJ
MDN = @load MDN pkg=MixtureDensityNetworks
mdn = MDN(mixtures=12, epochs=100, layers=[512, 256, 128])
X, y = make_regression(100, 1) # 合成データ
mach = machine(mdn, X, y) |> fit!
Xnew, _ = make_regression(3, 1)
ŷ = predict(mach, Xnew) # 新しい予測
report(mach).best_epoch # トレーニング中に遭遇した最良エポック 
report(mach).best_loss # トレーニング中に遭遇した最良損失 
training_losses(mach) # 学習曲線
```
