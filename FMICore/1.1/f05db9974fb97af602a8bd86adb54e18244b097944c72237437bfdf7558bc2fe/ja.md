ソース: FMISpec3.0, バージョン D5ef1c1: 2.2.10. 変数の依存関係

単一の未知の変数 vunknown が既知の変数 vknown に関連して持つ依存関係を定義する列挙型。これらは次の意味を持つ: 依存 - 特に構造はなく、f(.., v_{known,i}, ..)

浮動小数点型の未知数 v_{unknown} のみ:

定数 - 定数因子、c ⋅ v_{known,i} ここで c は fmi3EnterInitializationMode が呼び出される前に評価される式。

イベントおよび連続時間モード (ME) および通信ポイント (CS および SE) における浮動小数点型の未知数 v_{unknown} のみ、初期化モードの <InitialUnknown> には適用されない:

固定 - 固定因子、p⋅v_{known,i} ここで p は fmi3ExitInitializationMode が呼び出される前に評価される式。

調整可能 - 調整可能な因子、p⋅v_{known,i} ここで p は fmi3ExitInitializationMode が呼び出される前に評価され、イベントモードによるイベント処理 (ME) または通信ポイント (CS および SE) で評価される式。

離散 - 離散因子、d⋅v_{known,i} ここで d は fmi3ExitInitializationMode が呼び出される前に評価され、イベントモードによる外部または内部イベント、または通信ポイント (CS および SE) で評価される式。
