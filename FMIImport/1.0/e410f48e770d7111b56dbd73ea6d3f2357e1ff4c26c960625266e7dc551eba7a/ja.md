```
fmi2GetReal!(c::FMU2Component, vr::fmi2ValueReferenceFormat, values::AbstractArray{fmi2Real})
```

fmi2Real変数の配列の値を取得します。

指定されたフィールドに変数の実際の値を書き込みます。

# 引数

  * `c::fmi2Struct`: FMI 2.0.2標準におけるFMUの代表。

詳細: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `c::FMU2`: FMI 2.0.2標準におけるFMUとそのすべてのインスタンスを表す可変構造体。
  * `c::FMU2Component`: FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体。
  * `vr::fmi2ValueReferenceFormat`: ユーザーがfmi[X]ValueReferenceを渡す方法のワイルドカード。

詳細: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

  * `values::AbstractArray{fm2Real}`: 引数`values`は、これらの変数の実際の値を持つAbstractArrayです。

# 戻り値

  * `status::fmi2Status`: 戻り値`status`は`fmi2Status`型の列挙で、関数呼び出しの成功を示します。

詳細:

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが非同期に関数を実行する場合にこのステータスが返される

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.24]: 2.1.7 変数の値の取得と設定
  * FMISpec2.0.2[p.18]: 2.1.3 関数によって返されるステータス

また[`fmi2GetReal!`](@ref)も参照してください。
