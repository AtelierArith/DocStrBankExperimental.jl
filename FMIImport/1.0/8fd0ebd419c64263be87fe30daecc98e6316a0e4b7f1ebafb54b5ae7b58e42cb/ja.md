```
fmi3GetOutputDerivatives!(c::FMU3Instance, vr::AbstractArray{fmi3ValueReference}, nValueReferences::Csize_t, order::AbstractArray{fmi3Int32}, values::AbstractArray{fmi3Float64}, nValues::Csize_t)
```

出力値の n 番目の導関数を取得します。

# 引数

  * `c::FMU3Instance`: 可変構造体で、FMI 3.0 標準における FMU のインスタンス化されたインスタンスを表します。
  * `vr::Array{fmi3ValueReference}`: 引数 `vr` は、導関数を設定する変数を定義する「ValueReference」と呼ばれる `nValueReferences` の値ハンドルの配列です。
  * `nValueReferences::Csize_t`: 引数 `nValueReferences` は `vr` のサイズを定義します。
  * `order::Array{fmi3Int32}`: 引数 `order` は、実入力変数の導関数の対応する順序を指定する fmi3Int32 値の配列です。
  * `values::Array{fmi3Float64}`: 引数 `values` は、これらの変数の実際の値を持つ配列です。
  * `nValues::Csize_t`: 引数 `nValues` は `values` のサイズを定義します。

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙で、関数呼び出しの成功を示します。

詳細:

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMU を不可逆的に破損させるエラーが発生した場合

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.2.12. 連続出力の導関数を取得する

また [`fmi3GetOutputDerivatives!`](@ref) を参照してください。
