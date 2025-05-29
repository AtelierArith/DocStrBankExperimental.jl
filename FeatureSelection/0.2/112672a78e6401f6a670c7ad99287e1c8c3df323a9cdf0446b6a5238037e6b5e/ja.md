```
RecursiveFeatureElimination(model; n_features=0, step=1)
```

このモデルは、特徴選択のための再帰的特徴除去アルゴリズムを実装しています。再帰的に特徴を削除し、残りの特徴でベースモデルをトレーニングし、それらの重要性を評価して、所望の特徴数が選択されるまで続けます。

# トレーニングデータ

MLJまたはMLJBaseでは、インスタンス`rfe_model`をデータにバインドするには

```
mach = machine(rfe_model, X, y)
```

または、ベースモデルが重みをサポートしている場合は、次のようにします。

```
mach = machine(rfe_model, X, y, w)
```

ここで：

  * `X`は、ベースモデルが要求するスカイタイプの列を持つ任意の入力特徴のテーブル（例：`DataFrame`）です。列のスカイタイプは`schema(X)`で確認し、ベースモデルが要求する列のスカイタイプは`input_scitype(basemodel)`で確認します。
  * `y`はターゲットで、要素のスカイタイプが`Continuous`または`Finite`である任意の応答のテーブルです。これは、ベースモデルが要求する`target_scitype`によって異なります。スカイタイプは`scitype(y)`で確認します。
  * `w`は観測重みで、`nothing`（デフォルト）または要素のスカイタイプが`Count`または`Continuous`である`AbstractVector`です。これは、モデルのハイパーパラメータである`weights`カーネルとは異なります。以下を参照してください。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * model: 特徴の重要性に関する情報を提供する`fit`メソッドを持つベースモデル（すなわち`reports_feature_importances(model) == true`）
  * n_features::Real = 0: 選択する特徴の数。`0`の場合、特徴の半分が選択されます。正の整数の場合、パラメータは選択する特徴の絶対数です。0と1の間の実数の場合、選択する特徴の割合です。
  * step::Real=1: stepの値が少なくとも1の場合、各イテレーションで削除する特徴の量を示します。逆に、stepが0.0から1.0の範囲内に厳密にある場合、各イテレーションで削除する特徴の割合（切り捨て）を示します。

# 操作

  * `transform(mach, X)`: 入力テーブル`X`をRFEアルゴリズムによって受け入れられた特徴に対応する列のみを含む新しいテーブルに変換します。
  * `predict(mach, X)`: 入力テーブル`X`を上記の`transform(mach, X)`と同じ新しいテーブルに変換し、変換されたテーブルでフィットしたベースモデルを使用して予測します。

# フィットされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `features_left`: 再帰的特徴除去後に残った特徴の名前。
  * `model_fitresult`: ベースモデルのフィットされたパラメータ。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `scores`: トレーニングデータセット内の各特徴のスコアの辞書。モデルはスコアの高い変数をより重要と見なします。
  * `model_report`: フィットされたベースモデルのレポート。

# 例

以下の例では、アクティブなパッケージ環境にMLJDecisionTreeInterfaceがあると仮定します。

```
using MLJ

RandomForestRegressor = @load RandomForestRegressor pkg=DecisionTree

# ターゲットが入力テーブルの最初の5列のみに依存するデータセットを作成します。
A = rand(50, 10);
y = 10 .* sin.(
        pi .* A[:, 1] .* A[:, 2]
    ) + 20 .* (A[:, 3] .- 0.5).^ 2 .+ 10 .* A[:, 4] .+ 5 * A[:, 5];
X = MLJ.table(A);

# rfeモデルをフィットします：
rf = RandomForestRegressor()
selector = RecursiveFeatureElimination(rf, n_features=2)
mach = machine(selector, X, y)
fit!(mach)

# 特徴の重要性を表示します
feature_importances(mach)

# 削減された特徴セットでトレーニングされたベースモデルを使用して予測します：
Xnew = MLJ.table(rand(50, 10));
predict(mach, Xnew)

# すべての特徴を持つデータを削減された特徴セットに変換します：
transform(mach, Xnew)
```
