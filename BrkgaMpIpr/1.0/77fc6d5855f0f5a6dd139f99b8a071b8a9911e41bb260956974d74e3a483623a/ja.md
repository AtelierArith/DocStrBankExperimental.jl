```
kendall_tau_distance(vector1::Array{Float64, 1},
                     vector2::Array{Float64, 1};
                     stop_immediately::Bool = false)::Float64

kendall_tau_distance(vector1::SubArray{Float64, 1},
                     vector2::SubArray{Float64, 1};
                     stop_immediately::Bool = false)::Float64
```

2つのベクトル間の[Kendall Tau距離](https://en.wikipedia.org/wiki/Kendall_tau_distance)を計算します。

!!! note
    この関数は、順列染色体表現により適している場合があります。


# 引数

  * `vector1::Array{Float64, 1}`: 最初のベクトル。
  * `vector2::Array{Float64, 1}`: 2番目のベクトル。
  * `stop_immediately::Bool = false`: `true`の場合、違いを見つけた直後に計算を停止します。

# 例外

  * `ArgumentError`: `vector1`と`vector2`のサイズが異なる場合。
