```
getDefaultTolerance(md::fmi2ModelDescription)
```

DefaultExperimentから定義されている場合は許容誤差を返し、そうでなければ何も返しません。

# 引数

  * `md::fmi2ModelDescription`: ModelVariablesの静的情報を提供する構造体。

# 戻り値

  * `md.defaultExperiment.tolerance::Union{Real,Nothing}`: 定義されている場合はDefaultExperimentから実数値`tolerance`を返し、そうでなければ`nothing`を返します。
