```
ResourceEmit{T<:Real} <: Resource
```

排出可能な資源（*例*、CO₂、CH₄、NOₓ）。

これらの資源は、排出される資源として含めることができ、*例*、変数 [`emissions_strategic`](@ref man-opt_var-emissions) において。

# フィールド

  * **`id`** は資源の名前/識別子です。
  * **`co2_int::T`** はCO₂強度で、*例*、t/MWhです。
