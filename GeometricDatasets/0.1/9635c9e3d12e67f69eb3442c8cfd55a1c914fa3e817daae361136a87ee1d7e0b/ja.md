R^(`dim`)の立方体を`n`点と半径`radius`で作成します。

# 引数

  * `n::Integer`: 点の数。
  * `dim::Integer`: 立方体の次元（つまり、R^dimのどの次元にあるか）。
  * `radius::Number`: 立方体の「半径」、すなわち中心からその一方の面までの距離。
  * `noise::Function`: `y = noise(dim)`が`size(y) = (dim;)`の`Vector{<:Number}`である関数。
