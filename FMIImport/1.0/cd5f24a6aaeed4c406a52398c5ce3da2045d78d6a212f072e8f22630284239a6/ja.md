```
fmi2GetRealOutputDerivatives!(c::FMU2Component,  
                                vr::AbstractArray{fmi2ValueReference}, 
                                nvr::Csize_t, order::AbstractArray{fmi2Integer}, 
                                value::AbstractArray{fmi2Real})
```

実数入力変数の n 番目の時間導関数を設定します。

# 引数

  * `c::FMU2Component`: ミュータブル構造体で、FMI 2.0.2 標準の FMU のインスタンス化されたインスタンスを表します。
  * `vr::Array{fmi2ValueReference}`: 引数 `vr` は、導関数を設定する変数を定義する「ValueReference」と呼ばれる `nvr` 値ハンドルの配列です。
  * `nvr::Csize_t`: 引数 `nvr` は `vr` のサイズを定義します。
  * `order::Array{fmi2Integer}`: 引数 `order` は、実数入力変数の対応する導関数の順序を指定する fmi2Integer 値の配列です。
  * `values::Array{fmi2Real}`: 引数 `values` は、これらの変数の実際の値を持つ配列です。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMU を不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが非同期に関数を実行する場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義
  * FMISpec2.0.2[p.18]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.104]: 4.2.1 入力/出力値およびパラメータの転送

```
