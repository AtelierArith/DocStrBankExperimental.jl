```
fmi2SetReal(c::FMU2Component, vr::fmi2ValueReferenceFormat, values::Union{AbstractArray{<:Real}, <:Real})
```

実数変数の配列の値を設定します

# 引数

  * `c::fmi2Struct`: FMI 2.0.2 標準における FMU の代表。

詳細: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `c::FMU2`: FMI 2.0.2 標準における FMU とそのすべてのインスタンスを表す可変構造体。
  * `c::FMU2Component`: FMI 2.0.2 標準における FMU のインスタンス化されたインスタンスを表す可変構造体。
  * `vr::fmi2ValueReferenceFormat`: ユーザーが fmi[X]ValueReference を渡す方法のワイルドカード

詳細: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

  * `values::Union{Array{<:Real}, <:Real}`: 引数 `values` はこれらの変数の実際の値を持つ配列です。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙で、関数呼び出しの成功を示します。

詳細:

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMU を不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返される

関連情報として [`fmi2SetReal`](@ref) を参照してください。
