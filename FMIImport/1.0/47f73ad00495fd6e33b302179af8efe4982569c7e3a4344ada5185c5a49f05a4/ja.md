```
fmi2DoStep(c::FMU2Component, 
                communicationStepSize::Union{Real, Nothing} = nothing; 
                currentCommunicationPoint::Union{Real, Nothing} = nothing,
                noSetFMUStatePriorToCurrentPoint::Bool = true)
```

コシミュレーションFMUで1ステップを実行します

# 引数

  * `C::FMU2Component`: ミュータブル構造体で、FMI 2.0.2標準におけるFMUのインスタンスを表します。
  * `communicationStepSize::Union{Real, Nothing} = nothing`: 引数`communicationStepSize`は、`Real`型または`Nothing`型の値を含みます。引数が渡されない場合、デフォルト値`nothing`が使用されます。`communicationStepSize`は通信ステップサイズを定義します。

# キーワード

  * `currentCommunicationPoint::Union{Real, Nothing} = nothing`: 引数`currentCommunicationPoint`は、`Real`型または`Nothing`型の値を含みます。引数が渡されない場合、デフォルト値`nothing`が使用されます。`currentCommunicationPoint`はマスターの現在の通信ポイントを定義します。
  * `noSetFMUStatePriorToCurrentPoint::Bool = true`: 引数`noSetFMUStatePriorToCurrentPoint`は、`Boolean`型の値を含みます。引数が渡されない場合、デフォルト値`true`が使用されます。`noSetFMUStatePriorToCurrentPoint`は、このシミュレーション実行において`currentCommunicationPoint`より前の時刻に`fmi2SetFMUState`が呼び出されないかどうかを示します。

# 戻り値

  * `status::fmi2Status`: 戻り値`status`は`fmi2Status`型の列挙型で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: 問題なし
  * `fmi2Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行している場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.104]: 4.2.2 計算

[`fmi2DoStep`](@ref)も参照してください。
