半長軸を平均運動から計算します。

引数:

  * `n::Real`: 軌道の平均運動。[rad/s] または [deg/s]
  * `use_degrees:Bool`: `true` の場合、入力を度として解釈します。
  * `GM::Real`: 中心天体の重力定数。指定がない場合は `SatelliteDynamics.GM_EARTH` がデフォルトです。

戻り値:

  * `a::Real`: 半長軸。[m]
