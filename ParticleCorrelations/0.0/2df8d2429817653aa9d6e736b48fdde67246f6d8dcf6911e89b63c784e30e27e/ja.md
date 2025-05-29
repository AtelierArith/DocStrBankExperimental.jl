```
pair_radial_fun(pair_corr::Function, a12::T; polynomial_order::Int, mesh_size::Int)
```

関数 `pair_radial` を返します。`pair_radial(r1,r2, cos(θ12))` は、半径 r1 と r2 の間の粒子のペア相関を与え、彼らの間の角度は `θ12` です。

関数 `pair_radial` は、関数 `pair_corr_distance` から計算されます。ここで、`pair_corr_distance(sqrt(r1^2 + r2^2 - 2r1 * r2 * cos(θ12)))` はペア相関を与えます。
