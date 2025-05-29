```
boundariesRing(resol::Resolution, pix, step, T::Type{<:Real})
boundariesRing!(resol::Resolution, pix, step, buf::Matrix{T}) where {T <: Real}
```

与えられたピクセルの境界に沿った方向のセット（3Dベクトル）を、ある解像度のRINGスキームで計算します。

関数 `boundariesRing` は、RINGスキームでインデックス `pix` のピクセルの境界を指す $N$ ベクトルを含む型 `T` の $N \times 3$ 行列を返します。ピクセルの各エッジには `step` ポイントが含まれ、すべてのピクセルは4つのエッジを持つダイヤモンドのような形状をしているため、数 $N$ は `4 * step` に等しくなります。

この関数を何度も呼び出す予定がある場合は、結果を格納するために独自の行列を割り当て、`boundariesRing!` を呼び出すべきです。この関数は、結果が格納されるパラメータ `buf` を受け取ります。この行列の形状は `(4step, 3)` でなければならず、その要素は未定義のままにしておくことができます：

```julia
step = 10
buf = Matrix{Float64}(undef, 4step, 3)
boundariesRing!(res, pixidx, step, buf)  # これで `buf` が設定されます
```

# 例

ここでは、行列を二度割り当てるのを避けるために、`boundariesRing` と `boundariesRing!` を一緒に使用する方法を示します。

```julia-repl
julia> matr = boundariesRing(Resolution(16), 534, 2, Float16)
8×3 Matrix{Float16}:
 0.3535  -0.6123  0.707
 0.3525  -0.6353  0.687
 0.3513  -0.657   0.6665
 0.3762  -0.664   0.646
 0.4014  -0.6694  0.625
 0.4084  -0.645   0.646
 0.414   -0.6196  0.6665
 0.3843  -0.6167  0.687

julia> boundariesRing!(Resolution(16), 535, 2, matr)  # `matr` を再利用

julia> matr
8×3 Matrix{Float16}:
 0.4158  -0.5723  0.707
 0.415   -0.596   0.687
 0.414   -0.6196  0.6665
 0.4397  -0.624   0.646
 0.465   -0.627   0.625
 0.4697  -0.602   0.646
 0.473   -0.576   0.6665
 0.4446  -0.5747  0.687
```
