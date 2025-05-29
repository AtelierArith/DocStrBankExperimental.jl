```
getStartValue(md::fmi2ModelDescription, vrs::fmi2ValueReferenceFormat = md.valueReferences)
```

指定された値参照の開始/デフォルト値を返します。

# 引数

  * `md::fmi2ModelDescription`: モデル変数の静的情報を提供する構造体。
  * `vrs::fmi2ValueReferenceFormat = md.valueReferences`: ユーザーがfmi[X]ValueReferenceを渡す方法のワイルドカード（デフォルト = md.valueReferences）

詳細: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

# 戻り値

  * `starts::Array{fmi2ValueReferenceFormat}`: 指定された値参照の開始/デフォルト値

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2: 2.2.7 モデル変数の定義 (ModelVariables)
