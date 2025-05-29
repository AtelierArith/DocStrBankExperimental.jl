```
fmi2NewDiscreteStates(c::FMU2Component)
```

次の離散状態を返します

# 引数

  * `c::FMU2Component`: FMI 2.0.2 標準でインスタンス化された FMU のインスタンスを表す可変構造体。

# 戻り値

  * `eventInfo::fmi2EventInfo*`: `fmi2Boolean` 変数を持つ構造体

詳細は以下の通りです：

  * `newDiscreteStatesNeeded::fmi2Boolean`: `newDiscreteStatesNeeded = fmi2True` の場合、FMU はイベントモードに留まる必要があり、FMU は出力を計算して取得するために新しい入力を設定し、再度 `fmi2NewDiscreteStates` を呼び出す必要があります。すべての FMU が `newDiscreteStatesNeeded = fmi2False` を返す場合、`fmi2EnterContinuousTimeMode` を呼び出します。
  * `terminateSimulation::fmi2Boolean`: `terminateSimulation = fmi2True` の場合、`fmi2Terminate` を呼び出します。
  * `nominalsOfContinuousStatesChanged::fmi2Boolean`: `nominalsOfContinuousStatesChanged = fmi2True` の場合、関数呼び出しにより状態の名目値が変更され、`fmi2GetNominalsOfContinuousStates` で照会できます。
  * `valuesOfContinuousStatesChanged::fmi2Boolean`: `valuesOfContinuousStatesChanged = fmi2True` の場合、関数呼び出しにより連続状態ベクトルの少なくとも1つの要素がその値を変更しました。状態の新しい値は `fmi2GetContinuousStates` で取得できます。連続状態ベクトルの要素が値を変更していない場合、`valuesOfContinuousStatesChanged` は fmi2False を返さなければなりません。
  * `nextEventTimeDefined::fmi2Boolean`: `nextEventTimeDefined = fmi2True` の場合、シミュレーションは `time = nextEventTime` まで統合し、この時点で `fmi2EnterEventMode` を呼び出す必要があります。次のイベント時間の前に統合が停止された場合、`nextEventTime` の定義は無効になります。
  * `nextEventTime::fmi2Real`: 次のイベントは `nextEventTimeDefined=fmi2True` の場合

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.83]: 3.2.2 モデル方程式の評価

また、[`fmi2NewDiscreteStates`](@ref) も参照してください。
