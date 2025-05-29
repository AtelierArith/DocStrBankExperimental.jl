Source: FMISpec2.0.2[p.23]: 2.1.6 初期化、終了、およびFMUのリセット

FMUに初期化モードに入るよう指示します。この関数を呼び出す前に、属性が<ScalarVariable initial = "exact"または"approx">のすべての変数は、“fmi2SetXXX”関数を使用して設定できます（ScalarVariableの属性はモデル記述ファイルで定義されています。セクション2.2.7を参照）。他の変数を設定することは許可されていません。さらに、startTimeが定義されるために、fmi2EnterInitializationModeを呼び出す前にfmi2SetupExperimentを少なくとも1回呼び出す必要があります。
