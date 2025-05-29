```
fmi3GetBoolean(c::FMU3Instance, vr::fmi3ValueReferenceFormat)
```

fmi3Boolean変数の配列の値を取得します。

# 引数

  * `c::FMU3Instance`: FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体。
  * `vr::fmi3ValueReferenceFormat`: ユーザーがfmi[X]ValueReferenceを渡す方法のワイルドカード

詳細: `fmi3ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi3ValueReference, Array{fmi3ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

# 戻り値

  * `values::Array{fmi3Boolean}`: fmi3ValueReferenceFormatの長さの次元を持つfmi3Boolean変数の配列の値を返します。

# 出典

  * FMISpec3.0リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.2.6.2. 変数の値の取得と設定

また[`fmi3GetBoolean`](@ref)も参照してください。
