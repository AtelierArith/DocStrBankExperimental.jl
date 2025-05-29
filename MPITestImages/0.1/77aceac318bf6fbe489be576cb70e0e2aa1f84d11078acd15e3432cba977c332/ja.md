```julia
jaszczak_phantom(
    radiusSpheres,
    derenzoImage,
    height,
    distanceSpheresToRods,
    heightRods
)

```

ジャスチャックファントムを生成する関数です。最初にデレンゾファントムを生成する必要があります。これは生成する3Dボディの一部です。

# 引数

  * `radiusSpheres::Vector{Int64}`: ファントムの各球の半径を与える長さ6のベクター。
  * `derenzoImage::Matrix{Float64}`: ジャスチャックファントムの一部であるデレンゾファントム。

この画像の寸法は、結果として得られるファントムの深さと幅を決定します。

  * `height::Int64`: ファントムの高さ。
  * `distanceSpheresToRods::Int64`: 球と棒の始まりの間の距離。
  * `heightRods::Int64`: 棒の高さ（デレンゾファントム部分）。

# 戻り値

  * `Array{Float64, 3}`: 三次元ファントム。
