ソース: FMISpec2.0.2[p.49]: 2.2.7 モデル変数の定義 (ModelVariables)

変数の時間依存性を定義する列挙型、つまり、変数が値を変更できる時間の瞬間を定義します。

"constant": 変数の値は決して変わりません。 "fixed": 変数の値は初期化後に固定されます。つまり、fmi2ExitInitializationModeが呼び出された後、変数の値はもう変わりません。 "tunable": 変数の値は、因果関係が "parameter" または "input" で可変性が "tunable" の変数による外部イベント (ModelExchange) および通信ポイント (Co-Simulation) の間で一定です。可変性が "tunable" のパラメータまたは入力信号が変更されると、外部でイベントがトリガーされ (ModelExchange)、または次の通信ポイント (Co-Simulation) で変更が行われ、可変性が "tunable" で因果関係が "calculatedParameter" または "output" の変数は新たに計算されなければなりません。 "discrete": ModelExchange: 変数の値は外部および内部イベント (= FMUで暗黙的に定義された時間、状態、ステップイベント) の間で一定です。Co-Simulation: 通常、変数は「実際の」サンプリングデータシステムからのものであり、その値は通信ポイント (スレーブ内でも) でのみ変更されます。 "continuous": 型が "Real" の変数のみが "continuous" であることができます。ModelExchange: 値の変更に制限はありません。Co-Simulation: 通常、変数は微分方程式からのものであり、デフォルトは "continuous" です。列挙型の定数の再定義を助けるために、接頭辞 "fmi2" が追加されました。
