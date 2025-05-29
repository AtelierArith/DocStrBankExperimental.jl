```
fmi2GetString!(c::FMU2Component, vr::AbstractArray{fmi2ValueReference}, nvr::Csize_t, value::Union{AbstractArray{Ptr{Cchar}}, AbstractArray{Ptr{UInt8}}})
```

変数の値を取得および設定するための関数で、値参照によって識別されます。

これらの関数は、モデルが他のモデルに接続されている場合に、出力変数の実際の値を取得するために特に使用されます。

# 引数

  * `str::FMU2Component`: ミュータブル構造体で、FMI 2.0.2標準のFMUのインスタンス化されたインスタンスを表します。
  * `vr::AbstractArray{fmi2ValueReference}`: 引数 `vr` は、照会される変数を定義する「ValueReference」と呼ばれる `nvr` の値ハンドルの配列です。
  * `nvr::Csize_t`: 引数 `nvr` は `vr` のサイズを定義します。
  * `value::Union{AbstractArray{Ptr{Cchar}, AbstractArray{Ptr{UInt8}}}`: `value` 引数は、CcharまたはUInt8のデータを参照するメモリアドレスを持つ値のAbstractArrayであり、これらの変数の実際の値を持つベクトルを記述します。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙型で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが非同期に関数を実行している場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義
  * FMISpec2.0.2[p.18]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.24]: 2.1.7 変数の値の取得と設定

また、[`fmi2GetString!`](@ref)も参照してください。
