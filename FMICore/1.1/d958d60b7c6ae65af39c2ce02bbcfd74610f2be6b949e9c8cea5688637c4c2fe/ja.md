ソース: FMISpec3.0, バージョン D5ef1c1: 2.4.7.4. 変数属性列挙は、変数の時間依存性を定義します。言い換えれば、変数が値を変更できる時間の瞬間を定義します。[この属性の目的は、結果値を照会し、保存する必要がある時期を定義することです。たとえば、離散変数はイベント瞬間 (ME) または通信ポイント (CS および SE) でのみ値を変更するため、fmi3Get{VariableType} で照会し、イベント時に保存する必要があります。] この列挙の許可される値: constant - 変数の値は決して変わりません。

fixed - 変数の値は初期化後に固定されます。言い換えれば、fmi3ExitInitializationMode が呼び出された後、変数の値はもう変わりません。

tunable - 変数の値は、因果関係 = parameter および変動性 = tunable の変数によって、イベント (ME) および通信ポイント (CS および SE) の間で一定です。変動性 = tunable のパラメータが変更されると、外部でイベントがトリガーされます (イベントがサポートされている場合は ME または CS)、または変更は次の通信ポイント (CS および SE) で行われ、変動性 = tunable および因果関係 = calculatedParameter または output の変数は再計算されなければなりません。[tunable 入力は許可されていません。表 18 を参照してください。]

discrete - モデル交換: 変数の値は、外部および内部イベント (= FMU で暗黙的に定義された時間、状態、ステップイベント) の間で一定です。コ・シミュレーション: 通常、変数は実際のサンプリングデータシステムからのものであり、その値は通信ポイント (イベント処理を含む) でのみ変更されます。intermediateUpdate 中に、離散変数は変更されることは許可されません。[シミュレーションアルゴリズムが intermediateUpdate 中に離散変数の変更に気付いた場合、シミュレーションアルゴリズムは変更を遅延させ、earlyReturnRequested == fmi3True のイベントを発生させ、通信ポイント中に離散変数を変更でき、その後イベント処理が行われます。]

continuous - fmi3GetFloat32 または fmi3GetFloat64 型の変数のみが連続的です。モデル交換: 値の変更に制限はありません (セクション 4.1.1 を参照)。

デフォルトは、<Float32> および <Float64> 型の変数に対しては連続であり、他のすべての型に対しては離散です。

Clock 型およびクロック変数の型の変数に対しては、変動性は常に離散または調整可能です。

[連続状態に関する情報は、<ModelStructure> の <ContinuousStateDerivative> 要素で定義されていることに注意してください。]

列挙型の定数の再定義を助けるために、接頭辞 "fmi3" を追加しました。
