```
fmi2SetString(c::FMU2Component, vr::fmi2ValueReferenceFormat, values::Union{AbstractArray{String}, String})
```

文字列変数の配列の値を設定します

fmi2SetXXXを呼び出すことができる変数のタイプに関する正確なルールについては、FMISpec2.0.2のセクション2.2.7を参照してください。また、ModelExchangeの場合はFMISpec2.0.2のセクション3.2.3、CoSimulationの場合はFMISpec2.0.2のセクション4.2.4も参照してください。

# 引数

  * `c::FMU2Component`: ミュータブル構造体で、FMI 2.0.2標準のFMUのインスタンス化されたインスタンスを表します。
  * `vr::fmi2ValueReferenceFormat`: 引数`vr`は変数の値参照を定義します。

詳細: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

  * `values::Union{Array{String}, String}`: 引数`values`は、String型の配列または単一の値です。

# 戻り値

  * `status::fmi2Status`: 戻り値`status`は`fmi2Status`型の列挙体で、関数呼び出しの成功を示します。

詳細:

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが非同期に関数を実行する場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義
  * FMISpec2.0.2[p.18]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.24]: 2.1.7 変数の値の取得と設定
  * FMISpec2.0.2[p.46]: 2.2.7 モデル変数の定義
  * FMISpec2.0.2[p.46]: 3.2.3 呼び出しシーケンスの状態遷移
  * FMISpec2.0.2[p.108]: 4.2.4 マスターからスレーブへの呼び出しシーケンスの状態遷移

[`fmi2SetString`](@ref)も参照してください。
