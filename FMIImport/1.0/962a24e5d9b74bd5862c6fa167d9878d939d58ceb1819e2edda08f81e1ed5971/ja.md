```
fmi2GetString!(c::FMU2Component, vr::fmi2ValueReferenceFormat, values::AbstractArray{fmi2String})
```

指定されたフィールドにおける変数の配列の文字列値を書き込みます。

これらの関数は、モデルが他のモデルに接続されている場合に、出力変数の実際の値を取得するために特に使用されます。

# 引数

  * `str::fmi2Struct`: FMI 2.0.2標準におけるFMUの代表。

詳細: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `str::FMU2`: FMI 2.0.2標準におけるFMUとそのすべてのインスタンスを表す可変構造体。
  * `str::FMU2Component`: FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体。
  * `vr::fmi2ValueReferenceFormat`: 引数`vr`は変数の値参照を定義します。

詳細: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

  * `values::AbstractArray{fmi2String}`: 引数`values`は、これらの変数の実際の値を持つAbstractArrayです。

# 戻り値

  * 戻す値がない場合（Cのvoid関数のように）や、変数またはフィールドが値を持たない場合は、`Nothing`型のシングルトンインスタンスを返します。

# 出典

  * FMISpec2.0.2リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.24]: 2.1.7 変数の値の取得と設定
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義
  * FMISpec2.0.2[p.18]: 2.1.3 関数によって返されるステータス

[`fmi2GetString!`](@ref)も参照してください。
