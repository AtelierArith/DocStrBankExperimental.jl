天体中間極オフセットのx成分（`dX`）を[radians]で計算します。最初のEarthOrientationData引数が省略された場合、関数はデフォルトのモジュールグローバル値を使用します。

引数:

  * `eop::EarthOrientationData` オフセットを計算するために使用するEarthOrientationDataオブジェクト
  * `mjd::Real` `dX`値が必要なエポックのUTCにおける修正ユリウス日
  * `interp::Bool` 入力MJDにパラメータデータを線形補間するかどうか

返り値:

  * `dX::Float` ラジアンでの極オフセットのx成分。
