ソース: FMISpec2.0.2[p.85]: 3.2.2 モデル方程式の評価

この関数は、能力フラグ completedIntegratorStepNotNeeded = false が設定されている限り、積分器の各完了ステップ後に環境によって呼び出されなければなりません。enterEventMode == fmi2True の場合、イベントモードに入る必要があります。terminateSimulation == fmi2True の場合、シミュレーションは終了されなければなりません。
