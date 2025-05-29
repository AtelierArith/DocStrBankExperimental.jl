```
getDefaultStopTime(md::fmi2ModelDescription)
```

DefaultExperimentから定義されている場合はstopTimeを返し、そうでなければ何も返さない。

# 引数

  * `md::fmi2ModelDescription`: ModelVariablesの静的情報を提供する構造体。

# 戻り値

  * `md.defaultExperiment.stopTime::Union{Real,Nothing}`: 定義されている場合はDefaultExperimentから実数値の`stopTime`を返し、そうでなければ`nothing`を返す。
