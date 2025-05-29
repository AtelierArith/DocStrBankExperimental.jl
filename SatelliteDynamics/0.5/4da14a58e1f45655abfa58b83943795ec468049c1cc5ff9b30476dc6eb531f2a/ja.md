ポールの位置を計算します。x-およびy-成分を[radians]の単位でタプルとして返します。EarthOrientationData引数が省略された場合、関数はデフォルトのモジュールグローバル値を使用します。

引数:

  * `eop::EarthOrientationData` オフセットを計算するために使用するEarthOrientationDataオブジェクト
  * `mjd::Real` ポールロケーターが必要なエポックのUTCの修正ユリウス日。
  * `interp::Bool` 入力MJDにパラメータデータを線形補間するかどうか。

返すもの:

  * `pole_locator::Tuple{Float, Float}` (x, y) ラジアンでのポールの位置。
