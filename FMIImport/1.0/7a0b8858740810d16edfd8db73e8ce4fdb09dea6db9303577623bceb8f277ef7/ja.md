```
isModelStructureAvailable(md::fmi2ModelDescription)
```

FMUモデル記述に`dependency`情報が含まれている場合はtrueを返します。

# 引数

  * `md::fmi2ModelDescription`: モデル変数の静的情報を提供する構造体。

# 戻り値

  * `::Bool`: FMUモデル記述に`dependency`情報が含まれている場合はtrueを返します。
