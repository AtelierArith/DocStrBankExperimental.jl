```
GeneratorPRAS(; max_active_power, lump_renewable_generation) <: AbstractRAFormulation
```

# 引数

  * `max_active_power::String`: 最大アクティブ電力に使用する時系列の名前
  * `lump_renewable_generation::Bool`: 再生可能エネルギーの発電を地域にまとめるかどうか

GeneratorPRASはPRASにおける発電機のエントリを生成します。
