半長軸を与えて平均運動を計算します。

引数:

  * `a::Real`: 半長軸。 [m]
  * `use_degrees:Bool`: `true` の場合、結果を度の単位で返します
  * `GM::Real`: 中心天体の重力定数。指定がない場合は `SatelliteDynamics.GM_EARTH` がデフォルトです。

返り値:

  * `n::Real`: 軌道の平均運動。 [rad/s] または [deg/s]
