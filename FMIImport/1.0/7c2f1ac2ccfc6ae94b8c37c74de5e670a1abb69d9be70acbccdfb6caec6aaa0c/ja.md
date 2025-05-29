```
fmi2SetReal(c::FMU2Component, vr::AbstractArray{fmi2ValueReference}, nvr::Csize_t, value::AbstractArray{fmi2Real})
```

変数の値をその valueReference によって識別して取得および設定するための関数

# 引数

  * `c::FMU2Component`: ミュータブル構造体で、FMI 2.0.2 標準における FMU のインスタンス化されたインスタンスを表します。
  * `vr::AbstractArray{fmi2ValueReference}`: 引数 `vr` は `nvr` の値ハンドルの AbstractArray で、"ValueReference" と呼ばれ、照会される変数を定義します。
  * `nvr::Csize_t`: 引数 `nvr` は `vr` のサイズを定義します。
  * `values::AbstractArray{fm2Real}`: 引数 `values` はこれらの変数の実際の値を持つ AbstractArray です。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMU を不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが非同期に関数を実行する場合にこのステータスが返されます

関連情報として [`fmi2GetReal`](@ref) を参照してください。
