```
fmi2SetBoolean(c::FMU2Component, vr::AbstractArray{fmi2ValueReference}, nvr::Csize_t, value::AbstractArray{fmi2Boolean})
```

変数の値を取得および設定するための関数で、値参照によって識別されます。

# 引数

  * `c::FMU2Component`: 可変構造体で、FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表します。
  * `vr::AbstractArray{fmi2ValueReference}`: 引数 `vr` は、問い合わせる変数を定義する「ValueReference」と呼ばれる `nvr` の値ハンドルの配列です。
  * `nvr::Csize_t`: 引数 `nvr` は `vr` のサイズを定義します。
  * `value::AbstractArray{fmi2Boolean}`: 引数 `values` は、これらの変数の実際の値を持つ配列です。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返されます

関連情報として [`fmi2GetBoolean`](@ref) を参照してください。
