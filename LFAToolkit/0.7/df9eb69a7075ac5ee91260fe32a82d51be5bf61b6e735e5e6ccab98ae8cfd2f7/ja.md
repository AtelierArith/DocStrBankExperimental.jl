```julia
hale_trefethen_strip_transformation(ρ)
```

HaleとTrefethenのストリップ変換を計算します

# 引数:

  * `ρ::Float64`:  半短軸と半長軸の和

# 戻り値:

  * 準同型写像

# 例:

```jldoctest
# hale_trefethen_strip_transformation 準同型写像
g, gprime = hale_trefethen_strip_transformation(1.4);

# 検証
truegonrange = [-1.0, -0.36812132798370184, 0.0, 0.36812132798370184, 1.0];
@assert g.(LinRange(-1, 1, 5)) ≈ truegonrange

# 出力

```
