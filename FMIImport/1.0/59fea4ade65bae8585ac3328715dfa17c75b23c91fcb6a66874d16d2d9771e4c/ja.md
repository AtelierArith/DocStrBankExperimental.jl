```
fmi3GetShiftDecimal!(c::FMU3Instance, vr::AbstractArray{fmi3ValueReference}, nvr::Csize_t, shifts::AbstractArray{fmi3Float64})
```

fmi3GetShiftDecimalは、FMUから最初のClock tickまでの遅延を取得します。

# TODO 引数

# 引数

  * `c::FMU3Instance`: 引数 `c` は、FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体です。
  * `vr::AbstractArray{fmi3ValueReference}`: 引数 `vr` は、問い合わせる変数を定義する「ValueReference」と呼ばれる `nvr` の値ハンドルのAbstractArrayです。
  * `nvr::Csize_t`: 引数 `nvr` は、`vr` のサイズを定義します。
  * `shifts::AbstractArray{fmi3Float64}`:

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は、`fmi3Status` 型の列挙体で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: 問題なし
  * `fmi3Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.2.9. クロック

[`fmi3GetShiftDecimal!`](@ref) も参照してください。
