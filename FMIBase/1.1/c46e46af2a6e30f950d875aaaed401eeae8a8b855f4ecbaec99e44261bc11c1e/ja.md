```
getGenerationTool(md::fmi2ModelDescription)
```

モデル記述から'tag' 'generationtool'を返します。

# 引数

  * `md::fmi2ModelDescription`: モデル変数の静的情報を提供する構造体。

# 戻り値

  * `md.generationTool::Union{String, Nothing}`: モデル記述から'tag' 'generationtool'を返します。
