```
getModelIdentifier(md::fmiModelDescription; type=nothing)
```

CSまたはMEセクションから'tag'モデル識別子を返します。

# 引数

  * `md::fmi2ModelDescription`: モデル変数の静的情報を提供する構造体。

# キーワード

  * `type=nothing`: コシミュレーションまたはモデル交換が存在するかどうかを定義します。（デフォルト = nothing）

# 戻り値

  * `md.modelExchange.modelIdentifier::String`: モデル交換セクションから'tag'モデル識別子を返します。
  * `md.coSimulation.modelIdentifier::String`: コシミュレーションセクションから'tag'モデル識別子を返します。
