```
getDefaultStepSize(md::fmi2ModelDescription)
```

DefaultExperimentから定義されている場合はstepSizeを返し、そうでなければ何も返さない。

# 引数

  * `md::fmi2ModelDescription`: ModelVariablesの静的情報を提供する構造体。

# 戻り値

  * `md.defaultExperiment.stepSize::Union{Real,Nothing}`: 定義されている場合はDefaultExperimentから実数値`setpSize`を返し、そうでなければ`nothing`を返す。
