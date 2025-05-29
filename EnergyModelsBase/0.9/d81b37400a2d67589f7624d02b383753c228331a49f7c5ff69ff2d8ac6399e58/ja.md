```
ResourceCarrier{T<:Real} <: Resource
```

輸送および変換可能なリソース。これらのリソースは、*e.g*、変数 [`emissions_strategic`](@ref man-opt_var-emissions) において排出されるリソースとして含めることは**できません**。

# フィールド

  * **`id`** はリソースの名前/識別子です。
  * **`co2_int::T`** はCO₂強度で、*e.g*、t/MWhです。
