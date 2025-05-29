天体中間極オフセットのy成分（`dY`）を[radians]で計算します。最初のEarthOrientationData引数が省略された場合、関数はデフォルトのモジュールグローバル値を使用します。

引数:

  * `eop::EarthOrientationData` オフセットを計算するために使用するEarthOrientationDataオブジェクト
  * `mjd::Real` `dY`値が必要なエポックのUTCにおける修正ユリウス日
  * `interp::Bool` 入力MJDにパラメータデータを線形補間するかどうか

返り値:

  * `dY::Float` ラジアンでの極オフセットのy成分。
