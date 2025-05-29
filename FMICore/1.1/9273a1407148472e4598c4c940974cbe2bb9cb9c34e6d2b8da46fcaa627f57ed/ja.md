ソース: FMISpec3.0, バージョン D5ef1c1: 2.3.3. 状態: 初期化モード

連続状態の名目値を返します。

fmi3UpdateDiscreteStates が nominalsOfContinuousStatesChanged == fmi3True で返された場合、状態の少なくとも1つの名目値が変更されており、fmi3GetNominalsOfContinuousStates で照会できます。コシミュレーションおよびスケジュール実行では許可されていません。
