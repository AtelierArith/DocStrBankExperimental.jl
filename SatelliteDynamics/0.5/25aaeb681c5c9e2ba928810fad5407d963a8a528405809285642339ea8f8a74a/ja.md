x軸周りの回転行列。

引数：

  * `angle::Real`: 回転軸の正の方向を見たときの反時計回りの回転角。
  * `use_degrees:Bool`: `true` の場合、入力を度数法として解釈します。

戻り値：

  * `r::AbstractArray{<:Real, 2}`: 回転行列

参考文献：

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.27.
