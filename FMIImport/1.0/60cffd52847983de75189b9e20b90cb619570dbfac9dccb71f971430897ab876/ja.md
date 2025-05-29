```
fmi3SetIntervalDecimal(c::FMU3Instance, vr::AbstractArray{fmi3ValueReference}, nvr::Csize_t, intervals::AbstractArray{fmi3Float64})
```

次のクロックティックまでの間隔を設定します

# TODO 引数

# 引数

  * `c::FMU3Instance`: 引数 `c` は、FMI 3.0 標準における FMU のインスタンス化されたインスタンスを表す可変構造体です。
  * `vr::AbstractArray{fmi3ValueReference}`: 引数 `vr` は、問い合わせる変数を定義する「ValueReference」と呼ばれる `nvr` の値ハンドルの AbstractArray です。
  * `nvr::Csize_t`: 引数 `nvr` は `vr` のサイズを定義します。
  * `intervals::AbstractArray{fmi3Float64}`:

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙であり、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: 問題なし
  * `fmi3Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMU を不可逆的に破損させるエラーが発生した場合

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.2.9. クロック

[`fmi3SetIntervalDecimal`](@ref) も参照してください。
