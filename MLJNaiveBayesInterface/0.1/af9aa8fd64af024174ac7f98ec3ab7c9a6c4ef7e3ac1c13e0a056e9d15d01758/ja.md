```
GaussianNBClassifier
```

ガウスナイーブベイズ分類器を構築するためのモデルタイプで、[NaiveBayes.jl](https://github.com/dfdx/NaiveBayes.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
GaussianNBClassifier = @load GaussianNBClassifier pkg=NaiveBayes
```

`model = GaussianNBClassifier()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。

ターゲット変数`y`によって取られる各クラスに対して、入力変数`X`の条件付き確率分布は多変量ガウス分布であると仮定されています。これらのガウス分布の平均と共分散は最大尤度法を用いて推定され、ベイズの定理を適用することによって`X`が与えられたときの`y`の確率分布が導かれます。`y`の必要な周辺分布は、トレーニングデータにおけるクラス頻度を用いて推定されます。

**重要。** 「ナイーブベイズ分類器」という名前は、誤解を招く可能性があります。`y`が与えられたときの`X`の完全な多変量ガウス分布を学習しているため、通常のナイーブベイズ独立条件を適用しておらず、これは共分散行列を対角行列に強制することになります。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、列がスカイタイプ`Continuous`の入力特徴の任意のテーブル（例：`DataFrame`）です。列のスカイタイプは`schema(X)`で確認できます。
  * `y`は、要素のスカイタイプが`Finite`の任意の`AbstractVector`です。スカイタイプは`schema(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# 操作

  * `predict(mach, Xnew)`: 新しい特徴`Xnew`に対するターゲットの予測を返します。`X`と同じスカイタイプである必要があります。予測は確率的です。
  * `predict_mode(mach, Xnew)`: 上記の予測のモードを返します。

# フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `c_counts`: 各入力クラスの観測されたカウントを含む辞書。
  * `c_stats`: 各入力クラスに関する観測統計を含む辞書。各クラスは`DataStats`オブジェクトで表され、次のフィールドを持ちます。

      * `n_vars`: クラスの振る舞いを説明するために使用される変数の数。
      * `n_obs`: クラスが観測された回数。
      * `obs_axis`: 観測が計算された軸。
  * `gaussians`: 各クラスのガウス分布の辞書で、各クラスの分布を表します。Distributions.jlパッケージの`Distributions.MvNormal`型で表されます。
  * `n_obs`: トレーニングデータにおける観測の総数。

# 例

```
using MLJ
GaussianNB = @load GaussianNBClassifier pkg=NaiveBayes

X, y = @load_iris
clf = GaussianNB()
mach = machine(clf, X, y) |> fit!

fitted_params(mach)

preds = predict(mach, X) # 確率的予測
preds[1]
predict_mode(mach, X) # ポイント予測
```

[`MultinomialNBClassifier`](@ref)も参照してください。
