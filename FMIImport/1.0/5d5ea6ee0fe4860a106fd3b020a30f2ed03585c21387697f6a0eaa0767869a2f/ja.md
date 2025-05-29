```
fmi3SetInt32(c::FMU3Instance, vr::AbstractArray{fmi3ValueReference}, nvr::Csize_t, value::AbstractArray{fmi3UInt32}, nvalue::Csize_t)
```

変数の値を取得および設定するための関数で、値参照によって識別されます。

# 引数

  * `c::FMU3Instance`: 引数 `c` は、FMI 3.0 標準における FMU のインスタンス化されたインスタンスを表す可変構造体です。
  * `vr::AbstractArray{fmi3ValueReference}`: 引数 `vr` は、問い合わせる変数を定義する `nvr` の値ハンドル「ValueReference」の AbstractArray です。
  * `nvr::Csize_t`: 引数 `nvr` は `vr` のサイズを定義します。
  * `values::AbstractArray{fmi3UInt32}`: 引数 `values` は、これらの変数の実際の値を持つ AbstractArray です。
  * `nvalue::Csize_t`: 引数 `nvalue` は `values` のサイズを定義します。

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙で、関数呼び出しの成功を示します。

より詳細には:     - `fmi3OK`: すべて正常     - `fmi3Warning`: いくつかの問題があるが、計算は続行できる     - `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合     - `fmi3Error`: 通信ステップを全く実行できなかった場合     - `fmi3Fatal`: FMU を不可逆的に破損させるエラーが発生した場合

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.2.6.2. 変数値の取得と設定

また、[`fmi3SetUInt32`](@ref) も参照してください。
