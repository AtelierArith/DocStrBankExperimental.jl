```
getDefaultStartTime(md::fmi2ModelDescription)
```

DefaultExperimentから定義されている場合はstartTimeを返し、そうでなければnothingにデフォルトします。

# 引数

  * `md::fmi2ModelDescription`: ModelVariablesの静的情報を提供する構造体。

# 戻り値

  * `md.defaultExperiment.startTime::Union{Real,Nothing}`: 定義されている場合はDefaultExperimentから実数値`startTime`を返し、そうでなければ`nothing`にデフォルトします。
