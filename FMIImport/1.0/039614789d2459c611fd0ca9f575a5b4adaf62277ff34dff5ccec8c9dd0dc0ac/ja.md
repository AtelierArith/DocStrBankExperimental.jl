```
fmi2GetBoolean(c::FMU2Component, vr::fmi2ValueReferenceFormat)
```

fmi2Boolean変数の配列の値を取得します。

# 引数

  * `c::fmi2Struct`: FMI 2.0.2標準におけるFMUの代表。

詳細: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `c::FMU2`: FMI 2.0.2標準におけるFMUとそのすべてのインスタンスを表す可変構造体。
  * `c::FMU2Component`: FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体。
  * `vr::fmi2ValueReferenceFormat`: 引数`vr`は変数の値参照を定義します。

詳細: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

# 戻り値

  * `values::Array{fmi2Boolean}`: 戻り値`values`はこれらの変数の実際の値を持つ配列です。

また、[`fmi2GetBoolean!`](@ref)も参照してください。
