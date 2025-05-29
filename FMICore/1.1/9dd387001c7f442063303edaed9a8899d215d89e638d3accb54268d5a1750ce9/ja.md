ソース: FMISpec2.0.2[p.84]: 3.2.2 モデル方程式の評価

戻り値の引数 fmi2eventInfo.newDiscreteStatesNeeded が fmi2True の場合、FMU はイベントモードに留まる必要があり、FMU は出力を計算して取得するために新しい入力を FMU に設定する必要があります（入力に対して fmi2SetXXX）および再度 fmi2NewDiscreteStates を呼び出す必要があります。他の FMU との接続に応じて、環境は

  * いずれかの FMU から terminateSimulation = fmi2True が返された場合、fmi2Terminate を呼び出す必要があります。
  * すべての FMU が newDiscreteStatesNeeded = fmi2False を返す場合、fmi2EnterContinuousTimeMode を呼び出す必要があります。
  * それ以外の場合はイベントモードに留まります。

FMU が終了すると、終了の理由を説明する適切なメッセージがロガー関数によって印刷されると仮定されます（セクション 2.1.5 を参照）。もし nominalsOfContinuousStatesChanged = fmi2True であれば、状態の名目値は関数呼び出しによって変更され、fmi2GetNominalsOfContinuousStates で照会できます。もし valuesOfContinuousStatesChanged = fmi2True であれば、連続状態ベクトルの少なくとも1つの要素が関数呼び出しによってその値を変更しました。状態の新しい値は fmi2GetContinuousStates で取得するか、reinit = "true" の各状態について個別に getReal を呼び出すことで取得できます。連続状態ベクトルの要素がその値を変更していない場合、valuesOfContinuousStatesChanged は fmi2False を返さなければなりません。[この場合に fmi2True が返されると、無限イベントループが発生する可能性があります。] もし nextEventTimeDefined = fmi2True であれば、シミュレーションは最大で time = nextEventTime まで統合され、この時点で fmi2EnterEventMode を呼び出す必要があります。次のイベント時間の前に統合が停止した場合、たとえば状態イベントによって、nextEventTime の定義は無効になります。
