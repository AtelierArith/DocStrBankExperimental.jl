fmi2GetReal(c::FMU2Component, vr::fmi2ValueReferenceFormat)

fmi2Real変数の配列の値を取得します。

# 引数

  * `c::fmi2Struct`: FMI 2.0.2標準におけるFMUの代表。

詳細: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `c::FMU2`: FMI 2.0.2標準におけるFMUとそのすべてのインスタンスを表す可変構造体。
  * `c::FMU2Component`: FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体。
  * `vr::fmi2ValueReferenceFormat`: ユーザーがfmi[X]ValueReferenceを渡す方法のワイルドカード

詳細: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

# 戻り値

  * `values::Array{fm2Real}`: fmi2ValueReferenceFormatの長さの次元を持つfmi2Real変数の配列の値を返します。

# 出典

  * FMISpec2.0.2リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.24]: 2.1.7 変数の値の取得と設定
  * FMISpec2.0.2[p.18]: 2.1.3 関数によって返されるステータス

[`fmi2GetReal`](@ref)も参照してください。
