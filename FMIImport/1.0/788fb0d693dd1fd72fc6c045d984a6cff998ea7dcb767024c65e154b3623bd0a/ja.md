```
fmi2DoStep(c::FMU2Component, 
                currentCommunicationPoint::fmi2Real, 
                communicationStepSize::fmi2Real, 
                noSetFMUStatePriorToCurrentPoint::fmi2Boolean)
```

時間ステップの計算が開始されます。

# 引数

  * `c::FMU2Component`: ミュータブル構造体で、FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表します。
  * `currentCommunicationPoint::fmi2Real`: 引数 `currentCommunicationPoint` は、変数値の識別子である `fmi2Real` 型の値を含みます。 `currentCommunicationPoint` はマスターの現在の通信ポイントを定義します。
  * `communicationStepSize::fmi2Real`: 引数 `communicationStepSize` は、変数値の識別子である `fmi2Real` 型の値を含みます。 `communicationStepSize` は通信ステップサイズを定義します。

`noSetFMUStatePriorToCurrentPoint::Bool = true`: 引数 `noSetFMUStatePriorToCurrentPoint` は、Boolean 型の値を含みます。引数が渡されない場合、デフォルト値 `true` が使用されます。 `noSetFMUStatePriorToCurrentPoint` は、このシミュレーション実行において `currentCommunicationPoint` より前の時刻に `fmi2SetFMUState` が呼び出されないかどうかを示します。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙体で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが非同期に関数を実行している場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.104]: 4.2.2 計算

また、[`fmi2DoStep`](@ref)も参照してください。
