ソース: FMISpec3.0, バージョン D5ef1c1: 2.3.1. スーパー状態: FMU 状態設定可能

引数 fmuType は FMU のタイプを定義します:

  * fmi3ModelExchange: 初期化とイベントを持つ FMU; イベント間の連続システムのシミュレーションは、環境からの外部積分器を使用して行われます。
  * fmi3CoSimulation: コシミュレーションのためのブラックボックスインターフェース。
  * fmi3ScheduledExecution: 単一の計算リソース（例: CPUコア）上でのモデルパーティションの同時計算。
