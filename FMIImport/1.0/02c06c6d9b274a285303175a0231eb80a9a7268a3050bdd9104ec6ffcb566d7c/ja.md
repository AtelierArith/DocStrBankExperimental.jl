```
fmi2SetInteger(c::FMU2Component, vr::AbstractArray{fmi2ValueReference}, nvr::Csize_t, value::AbstractArray{fmi2Integer})
```

整数変数の配列の値を設定します

# 引数

  * `c::FMU2Component`: ミュータブル構造体で、FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表します。
  * `vr::AbstractArray{fmi2ValueReference}`: 引数 `vr` は、変数を問い合わせるために定義された `nvr` の値ハンドルのAbstractArrayである「ValueReference」です。
  * `nvr::Csize_t`: 引数 `nvr` は `vr` のサイズを定義します。
  * `values::AbstractArray{fmi2Integer}`: 引数 `values` は、これらの変数の実際の値を持つAbstractArrayです。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙体で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返されます

関連情報として [`fmi2GetInteger!`](@ref) を参照してください。

# ソース

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.24]: 2.1.7 変数値の取得と設定
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義
  * FMISpec2.0.2[p.18]: 2.1.3 関数によって返されるステータス
