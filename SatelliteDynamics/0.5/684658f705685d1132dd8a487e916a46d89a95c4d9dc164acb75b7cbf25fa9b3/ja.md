天体中間極（CIP）オフセット `(xp, yp)` を計算します。EarthOrientationData 引数が省略された場合、関数はデフォルトのモジュールグローバル値を使用します。

引数：

  * `eop::EarthOrientationData` オフセットを計算するために使用する EarthOrientationData オブジェクト
  * `mjd::Real` 極の位置を求めるためのエポックの UTC における修正ユリウス日
  * `interp::Bool` 入力 MJD にパラメータデータを線形補間するかどうか

戻り値：

  * `pole_offsets::Tuple{Float, Float}` (x, y) ラジアン単位の極の位置。
