航空ナビゲーションの目的で距離、角度、速度、ポイントを計算します。

すべての角度は度で、距離は標準でメートル、速度は標準でm/sです。

これらのメソッドは運用目的で使用されるべきではありません。

実装された関数：

  * distance
  * angular_distance
  * bearing
  * final_bearing
  * midpoint
  * intermediate_point
  * destination_point
  * intersection_point
  * along*track*distance
  * cross*track*distance
  * Vground
  * head_wind
  * cross_wind
  * normalize
  * closest*point*to_pole
  * isinside

実装された型：

  * Point(ϕ, λ)
  * Airspace

実装された定数：

  * Rₑ_m    地球の半径 [m]

基づいて：

  * source: www.movable-type.co.uk/scripts/latlong.html
  * source: edwilliams.org/avform.htm
