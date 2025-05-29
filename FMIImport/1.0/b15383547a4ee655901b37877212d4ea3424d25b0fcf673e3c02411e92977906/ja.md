```
fmi2GetReal!(c::FMU2Component, vr::AbstractArray{fmi2ValueReference}, nvr::Csize_t, value::AbstractArray{fmi2Real})
```

変数の値を取得および設定するための関数で、値参照によって識別されます。

# 引数

  * `c::FMU2Component`: 可変構造体で、FMI 2.0.2 標準における FMU のインスタンス化されたインスタンスを表します。
  * `vr::AbstractArray{fmi2ValueReference}`: 引数 `vr` は、問い合わせる変数を定義する `nvr` の値ハンドルを持つ AbstractArray です。
  * `nvr::Csize_t`: 引数 `nvr` は `vr` のサイズを定義します。
  * `values::AbstractArray{fm2Real}`: 引数 `values` は、これらの変数の実際の値を持つ AbstractArray です。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMU を不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行している場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.18]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.24]: 2.1.7 変数の値の取得と設定

また [`fmi2GetReal!`](@ref) を参照してください。
