```
fmi2GetInteger(c::FMU2Component, vr::fmi2ValueReferenceFormat)
```

変数の配列の整数値を返します

# 引数

  * `c::fmi2Struct`: FMI 2.0.2 標準における FMU の代表。

詳細: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `c::FMU2`: FMI 2.0.2 標準における FMU とそのすべてのインスタンスを表す可変構造体。
  * `c::FMU2Component`: FMI 2.0.2 標準における FMU のインスタンス化されたインスタンスを表す可変構造体。
  * `vr::fmi2ValueReferenceFormat`: 引数 `vr` は変数の値参照を定義します

詳細: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

# 戻り値

  * `values::Array{fmi2Integer}`: 戻り値 `values` はこれらの変数の実際の値を持つ配列です。

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.24]: 2.1.7 変数の値の取得と設定
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義
  * FMISpec2.0.2[p.18]: 2.1.3 関数によって返されるステータス

また、[`fmi2GetInteger!`](@ref) も参照してください
