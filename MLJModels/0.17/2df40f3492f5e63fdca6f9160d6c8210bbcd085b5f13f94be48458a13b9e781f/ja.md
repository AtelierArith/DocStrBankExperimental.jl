```
ConstantClassifier
```

この「ダミー」確率的予測器は、提供された入力パターンに関係なく、常に同じ分布を返します。返される分布 `d` は、トレーニングターゲットデータで観察されたクラスの頻度に基づく `UnivariateFinite` 分布です。したがって、`pdf(d, level)` は、トレーニングターゲットが値 `level` を取る回数です。トレーニングターゲットのモードを取得するには、`predict` の代わりに `predict_mode` を使用してください。`UnivariateFinite` 型の詳細については、CategoricalDistributions.jl パッケージを参照してください。

ほぼすべての合理的なモデルは、`ConstantClassifier` よりも優れた性能を発揮することが期待されており、これは主にテストやパフォーマンスベースラインの確立に使用されます。

MLJ（または MLJModels）では、`model = ConstantClassifier()` を実行してインスタンスを構築します。

# トレーニングデータ

MLJ または MLJBase では、次のようにしてインスタンス `model` をデータにバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X` は任意の入力特徴のテーブル（例：`DataFrame`）
  * `y` は、要素の scitype が `Finite` である任意の `AbstractVector` であり、`schema(y)` で scitype を確認します。

`fit!(mach, rows=...)` を使用してマシンをトレーニングします。

# ハイパーパラメータ

なし。

# 操作

  * `predict(mach, Xnew)`: 特徴 `Xnew` に基づいてターゲットの予測を返します（このモデルでは無視されます）。予測は確率的です。
  * `predict_mode(mach, Xnew)`: 上記で返された確率的予測のモードを返します。

# フィッティングされたパラメータ

`fitted_params(mach)` のフィールドは次のとおりです。

  * `target_distribution`: 提供されたターゲットデータにフィットした分布。

# 例

```julia
using MLJ

clf = ConstantClassifier()

X, y = @load_crabs # テーブルとカテゴリカルベクター
mach = machine(clf, X, y) |> fit!

fitted_params(mach)

Xnew = (;FL = [8.1, 24.8, 7.2],
        RW = [5.1, 25.7, 6.4],
        CL = [15.9, 46.7, 14.3],
        CW = [18.7, 59.7, 12.2],
        BD = [6.2, 23.6, 8.4],)

# 確率的予測：
yhat = predict(mach, Xnew)
yhat[1]

# 生の確率：
pdf.(yhat, "B")

# 確率行列：
L = levels(y)
pdf(yhat, L)

# ポイント予測：
predict_mode(mach, Xnew)
```

[`ConstantRegressor`](@ref) も参照してください。
