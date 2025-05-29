ポールロケーターのx成分を[radians]で計算します。最初のEarthOrientationData引数が省略された場合、関数はデフォルトのモジュールグローバル値を使用します。

引数:

  * `eop::EarthOrientationData` オフセットを計算するために使用するEarthOrientationDataオブジェクト
  * `mjd::Real` xp値が必要なエポックのUTCの修正ユリウス日。
  * `interp::Bool` 入力MJDにパラメータデータを線形補間するかどうか。

戻り値:

  * `xp::Float` ラジアンでのポールロケーターのx成分。
