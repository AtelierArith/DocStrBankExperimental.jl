ソース: FMISpec3.0, バージョン D5ef1c1: 2.3.2. 状態: インスタンス化

FMUに初期化モードに入るよう指示します。この関数を呼び出す前に、属性 <Datatype initial = "exact" または "approx"> を持つすべての変数は “fmi3SetXXX” 関数を使用して設定できます（スカラ変数の属性はモデル記述ファイルで定義されています。セクション 2.4.7 を参照）。他の変数を設定することは許可されていません。また、シミュレーションの開始時刻と終了時刻も設定します。
