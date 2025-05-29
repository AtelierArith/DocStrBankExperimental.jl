```
fmi3DoStep!(c::FMU3Instance, currentCommunicationPoint::Union{Real, Nothing} = nothing, communicationStepSize::Union{Real, Nothing} = nothing, noSetFMUStatePriorToCurrentPoint::Bool = true,
    eventEncountered::fmi3Boolean = fmi3False, terminateSimulation::fmi3Boolean = fmi3False, earlyReturn::fmi3Boolean = fmi3False, lastSuccessfulTime::fmi3Float64 = 0.0)
```

時間ステップの計算が開始されます。

# TODO 引数

# 引数

  * `c::FMU3Instance`: FMU 3.0標準におけるインスタンス化されたFMUを表す可変構造体。
  * `currentCommunicationPoint::Union{Real, Nothing} = nothing`
  * `communicationStepSize::Union{Real, Nothing} = nothing`
  * `noSetFMUStatePriorToCurrentPoint::Bool = true`
  * `eventEncountered::fmi3Boolean = fmi3False`
  * `terminateSimulation::fmi3Boolean = fmi3False`
  * `earlyReturn::fmi3Boolean = fmi3False`
  * `lastSuccessfulTime::fmi3Float64 = 0.0`

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙であり、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 4.2.1. 状態: ステップモード

さらに [`fmi3DoStep!`](@ref) を参照してください。
