```
ProblemTemplate(::Type{T}) where {T<:PM.AbstractPowerFormulation}
```

PowerSimulations最適化問題のモデル参照を作成します。

# 引数

  * `model::Type{T<:PM.AbstractPowerFormulation}`:

# 例

template = ProblemTemplate(CopperPlatePowerModel)
