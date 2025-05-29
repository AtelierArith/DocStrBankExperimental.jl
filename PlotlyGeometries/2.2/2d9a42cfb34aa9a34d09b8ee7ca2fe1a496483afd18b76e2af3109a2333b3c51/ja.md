```
grot!(geo::GenericTrace, rotang::Vector{<:Real}, center::Vector{<:Real}=[0])

指定された中心点の周りに3Dジオメトリを回転させます。（テイト–ブライアン回転）

# 引数
- `geo::GenericTrace`: 回転させる3Dジオメトリで、`x`、`y`、および`z`座標を持っている必要があります。
- `rotang::Vector{<:Real}`: x、y、z軸の周りの回転のための3つのテイト–ブライアン回転角度のベクトル（度単位）。
- `center::Vector{<:Real}`: 回転の中心点。デフォルトは`[0]`で、これは回転中心がオブジェクトの幾何学的中心に設定されることを意味します。
```
