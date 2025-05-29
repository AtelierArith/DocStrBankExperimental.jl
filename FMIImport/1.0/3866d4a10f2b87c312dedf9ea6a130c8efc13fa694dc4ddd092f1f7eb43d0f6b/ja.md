```
fmi2SetBoolean(c::FMU2Component, vr::fmi2ValueReferenceFormat, values::Union{AbstractArray{Bool}, Bool})
```

ブール変数の配列の値を設定します

# 引数

  * `c::FMU2Component`: 可変構造体で、FMI 2.0.2 標準におけるインスタンス化された FMU のインスタンスを表します。
  * `vr::fmi2ValueReferenceFormat`: 引数 `vr` は変数の値参照を定義します。

詳細: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

  * `values::Union{Array{Bool}, Bool}`: 引数 `values` はブール型の配列または単一の値です。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙で、関数呼び出しの成功を示します。

詳細:

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMU を不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが非同期に関数を実行する場合にこのステータスが返されます

関連情報として [`fmi2GetBoolean!`](@ref) を参照してください。
