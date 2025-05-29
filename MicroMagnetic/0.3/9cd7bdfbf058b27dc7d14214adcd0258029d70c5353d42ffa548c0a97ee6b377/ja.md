```
compute_magnetic_phase(m::Array{T,4}, theta::Real, axis::String;
```

N1::Int=-1, N2::Int=-1, Ms=1/mu_0, d::Real=1.0) where {T<:AbstractFloat}

磁化配列から磁気位相を計算します。

## パラメータ

m: サイズ (3, nx, ny, nz) の 4D 配列。磁化配列。 theta: オイラー角。 axis: "X" または "Y" から選択された回転軸 N1: 投影計算時のパディングサイズ N2: フーリエ変換カーネルのパディングサイズ、デフォルトは 2*N1

## 出力

phi: サイズ (N,N) の 2D 配列。磁気位相。 ```
