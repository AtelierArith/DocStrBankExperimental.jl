```
fmi2SetInteger(c::FMU2Component, vr::fmi2ValueReferenceFormat, values::Union{AbstractArray{<:Integer}, <:Integer})
```

整数変数の配列の値を設定します

# 引数

  * `c::fmi2Struct`: FMI 2.0.2 標準における FMU の代表。

詳細: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `c::FMU2`: FMI 2.0.2 標準における FMU とそのすべてのインスタンスを表す可変構造体。
  * `c::FMU2Component`: FMI 2.0.2 標準における FMU のインスタンスを表す可変構造体。
  * `vr::fmi2ValueReferenceFormat`: 引数 `vr` は変数の値参照を定義します。

詳細: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

  * `vr::Array{fmi2ValueReference}`: 引数 `vr` は、問い合わせる変数を定義する「ValueReference」と呼ばれる `nvr` の値ハンドルの配列です。
  * `values::Union{Array{<:Integer}, <:Integer}`: 引数 `values` は、整数型またはそのサブタイプの単一の値または配列です。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は関数呼び出しの成功を示します。

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.24]: 2.1.7 変数の値の取得と設定
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義
  * FMISpec2.0.2[p.18]: 2.1.3 関数によって返されるステータス

また [`fmi2SetInteger`](@ref) を参照してください。 ```
