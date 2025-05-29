```
fmi2NewDiscreteStates!(c::FMU2Component, eventInfo::fmi2EventInfo)
```

FMUはイベントモードにあり、この呼び出しによって超密な時間が増加します。

# 引数

  * `c::FMU2Component`: FMI 2.0.2標準のFMUのインスタンスを表す可変構造体。
  * `eventInfo::fmi2EventInfo*`: `fmi2Boolean`変数を持つ構造体で

詳細:

  * `newDiscreteStatesNeeded::fmi2Boolean`: `newDiscreteStatesNeeded = fmi2True`の場合、FMUはイベントモードに留まる必要があり、FMUは出力を計算して取得するために新しい入力を設定し、再度`fmi2NewDiscreteStates`を呼び出す必要があります。すべてのFMUが`newDiscreteStatesNeeded = fmi2False`を返す場合、`fmi2EnterContinuousTimeMode`を呼び出します。
  * `terminateSimulation::fmi2Boolean`: `terminateSimulation = fmi2True`の場合、`fmi2Terminate`を呼び出します。
  * `nominalsOfContinuousStatesChanged::fmi2Boolean`: `nominalsOfContinuousStatesChanged = fmi2True`の場合、関数呼び出しにより状態の名目値が変更され、`fmi2GetNominalsOfContinuousStates`で照会できます。
  * `valuesOfContinuousStatesChanged::fmi2Boolean`: `valuesOfContinuousStatesChanged = fmi2True`の場合、関数呼び出しにより連続状態ベクトルの少なくとも1つの要素がその値を変更しました。状態の新しい値は`fmi2GetContinuousStates`で取得できます。連続状態ベクトルの要素が値を変更していない場合、`valuesOfContinuousStatesChanged`はfmi2Falseを返さなければなりません。
  * `nextEventTimeDefined::fmi2Boolean`: `nextEventTimeDefined = fmi2True`の場合、シミュレーションは`time = nextEventTime`まで統合し、この時点で`fmi2EnterEventMode`を呼び出す必要があります。次のイベント時間の前に統合が停止された場合、`nextEventTime`の定義は無効になります。
  * `nextEventTime::fmi2Real`: 次のイベントは`nextEventTimeDefined=fmi2True`の場合

# 戻り値

  * `status::fmi2Status`: 戻り値`status`は`fmi2Status`型の列挙で、関数呼び出しの成功を示します。

詳細:

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
  * FMISpec2.0.2[p.83]: 3.2.2 モデル方程式の評価

また[`fmi2NewDiscreteStates`](@ref)を参照してください。
