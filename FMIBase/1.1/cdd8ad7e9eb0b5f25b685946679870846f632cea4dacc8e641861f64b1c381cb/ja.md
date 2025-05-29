```
getModelVariableIndices(md::fmi2ModelDescription; vrs=md.valueReferences)
```

値参照 `vrs` に対応するインデックスの配列を返します。

# 引数

  * `md::fmi2ModelDescription`: モデル変数の静的情報を提供する構造体。

# キーワード

  * `vrs=md.valueReferences`: モデル記述の追加属性 `valueReferences::Array{fmi2ValueReference}` で、(基本型) 変数値へのハンドルです。ハンドルと基本型は変数の値を一意に識別します。(デフォルト = `md.valueReferences::Array{fmi2ValueReference}`)

# 戻り値

  * `names::Array{Integer}`: 値参照 `vrs` に対応するインデックスの配列を返します。
