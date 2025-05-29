```
fmi2GetBoolean!(c::FMU2Component, vr::AbstractArray{fmi2ValueReference}, nvr::Csize_t, value::AbstractArray{fmi2Boolean})
```

指定されたフィールドにおける変数の配列のブール値を書き込みます。

fmi2GetBoolean!は値の配列に対してのみ可能です。スカラーの代わりに配列を使用してください。

# 引数

  * `c::FMU2Component`: 可変構造体で、FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表します。
  * `vr::AbstractArray{fmi2ValueReference}`: 引数`vr`は、問い合わせる変数を定義する`nvr`の値ハンドル「ValueReference」のAbstractArrayです。
  * `nvr::Csize_t`: 引数`nvr`は`vr`のサイズを定義します。
  * `value::AbstractArray{fmi2Boolean}`: 引数`values`は、これらの変数の実際の値を持つ配列です。

# 戻り値

  * `status::fmi2Status`: 戻り値`status`は`fmi2Status`型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返されます

関連情報として[`fmi2GetBoolean!`](@ref)も参照してください。

# ソース

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.24]: 2.1.7 変数値の取得と設定
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義
  * FMISpec2.0.2[p.18]: 2.1.3 関数によって返されるステータス
