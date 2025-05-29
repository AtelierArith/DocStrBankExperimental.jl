```
FullModel{M, N} <: AnovaModel{M, N}
```

ANOVAを実施するための回帰モデルのラッパーです。

  * `M` は回帰モデルの型です。
  * `N` は予測子の数です。

# フィールド

  * `model`: 回帰モデル。
  * `pred_id`: ANOVAに含まれる項のインデックス。ソースイテラブルは `predictors(model)` によって取得できます。この値は、特定のモデルに対して `type` に依存する場合があります。例えば、逆リンクを持つガンマ回帰モデルのタイプ1 ANOVAなどです。
  * `type`: ANOVAのタイプ、1、2、または3のいずれかです。

# コンストラクタ

```
FullModel(model::RegressionModel, type::Int, null::Bool, test_intercept::Bool)
```

  * `model`: 回帰モデル。
  * `type`: ANOVAのタイプ、1、2、または3のいずれかです。
  * `null`: `y ~ 0` が許可されるかどうか。
  * `test_intercept`: 切片がテストされるかどうか。
