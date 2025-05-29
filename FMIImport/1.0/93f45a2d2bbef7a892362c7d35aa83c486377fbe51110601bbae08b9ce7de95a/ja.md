```
isModelStructureDerivativesAvailable(md::fmi2ModelDescription)
```

FMUモデル記述が`derivatives`のための`dependency`情報を含んでいるかどうかを返します。

# 引数

  * `md::fmi2ModelDescription`: モデル変数の静的情報を提供する構造体。

# 戻り値

  * `::Bool`: FMUモデル記述が`derivatives`のための`dependency`情報を含んでいる場合はtrueを返します。
