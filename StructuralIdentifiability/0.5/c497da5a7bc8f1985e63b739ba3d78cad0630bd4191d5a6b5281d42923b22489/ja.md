```
assess_identifiability(ode; funcs_to_check = [], prob_threshold=0.99, loglevel=Logging.Info)
```

入力:

  * `ode` - ODEモデル
  * `funcs_to_check` - 同定可能性を確認する関数のリスト; 空の場合、すべてのパラメータと状態が考慮される
  * `known_ic`: 初期条件が既知であると仮定される関数のリスト。返される同定可能な関数は、状態ではなくパラメータと初期条件の関数となる（これは実験的な機能です）。
  * `prob_threshold` - 正確性の確率。
  * `loglevel` - 表示するログメッセージの最小レベル（デフォルトは`Logging.Info`）

与えられたODEモデルの同定可能性を評価します。結果は、少なくとも`prob_threshold`の確率で正しいことが保証されます。この関数は、確認する関数からその同定可能性の特性（`:nonidentifiable`、`:locally`、`:globally`のいずれか）への（順序付き）辞書を返します。
