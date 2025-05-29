```
hamming_distance(vector1::Array{Float64, 1}, vector2::Array{Float64, 1},
                 threshold::Float64 = 0.5)::Float64
```

2つのベクトル間の[ハミング距離](https://en.wikipedia.org/wiki/Hamming_distance)を計算します。ベクトルを「バイナライズ」するための`threshold`パラメータを取ります。例えば、`threshold = 0.7`の場合、0.7以上のすべての値は`1.0`と見なされ、それ以外は`0.0`となります。

!!! note
    この関数は、しきい値/直接的な染色体表現により適しているかもしれません。


# 引数

  * `vector1::Array{Float64, 1}`: 最初のベクトル。
  * `vector2::Array{Float64, 1}`: 2番目のベクトル。
  * `threshold::Float64 = 0.5`: バイナライズのためのしきい値。

# 例外

  * `ArgumentError`: `vector1`と`vector2`のサイズが異なる場合。
