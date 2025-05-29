```julia
delta_image(
    size,
    numOfPoints;
    sizeOfPoint,
    distanceOfPoints,
    pivot,
    circularShape
)

```

離散点を持つファントムを生成する関数です。`distanceOfPoints`引数は、生成する点の番号を受け取り整数を返す2つの関数を取ります。これにより、生成されるファントムは非常にカスタマイズ可能になります。

# 引数

  * `size::Tuple{Integer, Integer}`: ファントムのサイズ
  * `numOfPoints::Integer`: 生成する点の数
  * `sizeOfPoint::Tuple{Integer, Integer}`: ファントム内の点のサイズ
  * `distanceOfPoints::Tuple{Function, Function}`: x方向とy方向の各点間に追加する距離
  * `pivot::Tuple{Integer, Integer}`: 点を生成するための開始点 (size, size)
  * `circularShape::Bool`: trueの場合、点は円形に生成されます

# 例

## 2つのシンプルなドット

```jldoctest
julia> image = delta_image((8, 8), 2; sizeOfPoint=(3, 2), distanceOfPoints=(x -> 0, x -> 4), pivot=(3, 3))
8×8 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  1.0  0.0  0.0  1.0  1.0
 0.0  0.0  1.0  1.0  0.0  0.0  1.0  1.0
 0.0  0.0  1.0  1.0  0.0  0.0  1.0  1.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
```

## L字型の配置

```jldoctest
julia> image = delta_image((8, 8), 3; sizeOfPoint=(2, 2), distanceOfPoints=(x -> x == 2 ? 3 : 0, x -> x == 3 ? -3 : 3), pivot=(3, 3))
8×8 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  1.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  1.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  1.0  0.0  1.0  1.0  0.0
 0.0  0.0  1.0  1.0  0.0  1.0  1.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
```
