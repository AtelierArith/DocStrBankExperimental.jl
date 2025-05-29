衛星の軌道周期を半長軸から計算します。

引数:

  * `a::Real`: 半長軸。 [m]
  * `GM::Real`: 中心天体の重力定数。指定がない場合は `SatelliteDynamics.GM_EARTH` がデフォルトです。

返り値:

  * `T::Real`: 軌道周期。 [s]
