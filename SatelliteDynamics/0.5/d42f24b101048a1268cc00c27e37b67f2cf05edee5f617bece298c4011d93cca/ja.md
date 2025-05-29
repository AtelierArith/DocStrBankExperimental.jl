UT1とUTCの時間システム間のオフセットを秒単位で計算します。EarthOrientationData引数が省略された場合、関数はデフォルトのモジュールグローバル値を使用します。

引数:

  * `eop::EarthOrientationData` オフセットを計算するために使用するEarthOrientationDataオブジェクト
  * `mjd::Real` UT1-UTCオフセットが必要なエポックのUTCにおける修正ユリウス日
  * `interp::Bool` 入力MJDにパラメータデータを線形補間するかどうか

戻り値:

  * `ut1_utc::Float` UT1 - UTCオフセット。[s]
