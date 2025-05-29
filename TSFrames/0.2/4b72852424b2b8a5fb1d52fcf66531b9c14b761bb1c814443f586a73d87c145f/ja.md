# 非インデックスデータを行列に変換する

TSFrameオブジェクトの非インデックス列のデータは、`Matrix()`コンストラクタを使用して、さらなる数値分析のために`Matrix`型に変換できます。

# 例

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random, Statistics)
julia> using Random;
julia> random(x) = rand(MersenneTwister(123), x);
julia> ts = TSFrame([random(10) random(10)])
julia> show(ts)
(10 x 2) TSFrame with Int64 Index

 Index  x1         x2
 Int64  Float64    Float64
─────────────────────────────
     1  0.768448   0.768448
     2  0.940515   0.940515
     3  0.673959   0.673959
     4  0.395453   0.395453
     5  0.313244   0.313244
     6  0.662555   0.662555
     7  0.586022   0.586022
     8  0.0521332  0.0521332
     9  0.26864    0.26864
    10  0.108871   0.108871

julia> Matrix(ts)
10×2 Matrix{Float64}:
 0.768448   0.768448
 0.940515   0.940515
 0.673959   0.673959
 0.395453   0.395453
 0.313244   0.313244
 0.662555   0.662555
 0.586022   0.586022
 0.0521332  0.0521332
 0.26864    0.26864
 0.108871   0.108871
```
