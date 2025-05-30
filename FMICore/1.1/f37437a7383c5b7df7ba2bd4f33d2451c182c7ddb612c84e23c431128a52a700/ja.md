ソース: FMISpec3.0, バージョン D5ef1c1: 3.2.1. 状態: 連続時間モード

この関数は、能力フラグ needsCompletedIntegratorStep = true が必要な場合、環境によって積分器の各完了ステップの後に呼び出されなければなりません。enterEventMode == fmi3True の場合、イベントモードに入る必要があります。terminateSimulation == fmi3True の場合、シミュレーションは終了しなければなりません。
