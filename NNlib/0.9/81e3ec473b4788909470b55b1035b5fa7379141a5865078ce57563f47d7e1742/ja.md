```
∇imrotate(dy, arr::AbstractArray{T, 4}, θ; method=:bilinear,
                                           rotation_center=size(arr) .÷ 2 .+ 1)
```

`imrotate`の随伴。`arr`に対してのみ勾配を計算し、`θ`には影響しません。

# 引数

  * `dy`: 入力勾配
  * `arr`: プライマル計算からの入力
  * `θ`: ラジアンでの回転角
  * `method=:bilinear` または `method=:nearest`
  * `rotation_center=size(arr) .÷ 2 .+ 1` 偶数および奇数サイズの配列に対して実際の中心ピクセルの周りで回転します
