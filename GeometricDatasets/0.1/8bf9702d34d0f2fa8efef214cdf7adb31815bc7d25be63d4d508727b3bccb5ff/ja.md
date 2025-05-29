R^(`dim`)の球を`n`点と半径`radius`で作成します。

# 引数

  * `n::Integer`: 点の数。
  * `dim::Integer`: 球の次元（すなわち、R^dimの中で）。
  * `radius::Number`: 球の半径。
  * `noise::Function`: `y = noise(dim)`が`size(y) = (dim;)`の`Vector{<:Number}`である関数。
