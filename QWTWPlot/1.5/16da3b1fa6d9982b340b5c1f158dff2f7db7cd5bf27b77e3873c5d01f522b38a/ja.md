```
qspectrogram_info(ymin::Float64, ymax::Float64, xmin::Float64, xmax::Float64, z::Matrix{Float64}; p::AbstractArray{Float64, 3} = zeros(1, 1, 1), t::Matrix{Float64} = [0.0 0.0])::Int32
```

パラメータ:

  * xmin 最小 x 座標
  * xmax 最大 x 座標
  * ymin 最小 y 座標
  * ymax 最大 y 座標
  * z スペクトログラム情報。[ny x nx] 行列
  * p 各ピクセルに関連付けられた 3D 配列 [3 x ny x nx] Float64 配列
  * tt 各ピクセルに関連付けられたパラメータ（タイムスタンプ？）値 [ny x nx] Float64 行列
