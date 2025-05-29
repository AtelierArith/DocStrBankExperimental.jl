与えられたエポックでの衛星状態をSGP4伝播器から出力として計算します。

引数:

  * `tle::TLE` 二行要素オブジェクト
  * `epc::Epoch` SGP4状態のエポック
  * `opscode::Char` 伝播器の運用モード

戻り値:

  * `rv::AbstractArray{Float64, 1}` TLE伝播器によって出力された位置と速度。単位 [m m/s]
