```
change(model::Physics, property, value) => updatedModel::Physics
```

既存の `Physics` モデルのプロパティを変更するための便利な関数です。

# 入力引数

  * `model::Physics` 修正する `Physics` モデル
  * `property` 変更するプロパティを指定するシンボル
  * `value` 指定された `property` の新しい設定

# 出力

この関数は新しい `Physics` オブジェクトを返します。

# 例

モデルを変更して、定常状態で収束した後に過渡シミュレーションを実行するための例

```
modelTransient = change(model, :time, Transient())
```
