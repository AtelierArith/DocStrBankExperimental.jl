```
ConstantRegressor
```

この「ダミー」確率的予測器は、提供された入力パターンに関係なく、常に同じ分布を返します。返される分布は、トレーニングターゲットデータに最も適合する指定されたタイプのものです。代わりに平均値または中央値を予測するには、`predict_mean`または`predict_median`を使用してください。指定されていない場合、正規分布がフィットされます。

ほぼすべての合理的なモデルは、`ConstantRegressor`よりも優れた性能を発揮することが期待されており、これはほぼ専らテストおよびパフォーマンスベースラインの確立に使用されます。

MLJ（またはMLJModels）では、`model = ConstantRegressor()`または`model = ConstantRegressor(distribution=...)`を実行してモデルインスタンスを構築します。

# トレーニングデータ

MLJ（またはMLJBase）では、インスタンス`model`をデータにバインドするには

```
mach = machine(model, X, y)
```

ここで：

  * `X`は任意の入力特徴のテーブル（例：`DataFrame`）
  * `y`は、要素のscitypeが`Continuous`である任意の`AbstractVector`です。scitypeは`schema(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `distribution_type=Distributions.Normal`: ターゲットデータにフィットさせる分布。`Distributions.ContinuousUnivariateDistribution`のサブタイプでなければなりません。

# 操作

  * `predict(mach, Xnew)`: 特徴`Xnew`（このモデルでは無視されます）を考慮してターゲットの予測を返します。予測は確率的です。
  * `predict_mean(mach, Xnew)`: 上記で返された確率的予測の平均を代わりに返します。
  * `predict_median(mach, Xnew)`: 上記で返された確率的予測の中央値を代わりに返します。

# フィットされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです：

  * `target_distribution`: 提供されたターゲットデータにフィットした分布。

# 例

```julia
using MLJ

X, y = make_regression(10, 2) # 合成データ：テーブルとベクトル
regressor = ConstantRegressor()
mach = machine(regressor, X, y) |> fit!

fitted_params(mach)

Xnew, _ = make_regression(3, 2)
predict(mach, Xnew)
predict_mean(mach, Xnew)

```

[`ConstantClassifier`](@ref)も参照してください。
