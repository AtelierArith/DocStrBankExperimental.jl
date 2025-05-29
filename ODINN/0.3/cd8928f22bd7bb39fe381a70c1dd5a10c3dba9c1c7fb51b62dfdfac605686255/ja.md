```
InversionParameters{F<:AbstractFloat}(;
    initial_conditions::Vector{F} = [1.0],
    lower_bound::Vector{F} = [0.0],
    upper_bound::Vector{F} = [Inf],
    regions_split::Vector{Int} = [1, 1],
    x_tol::F = 1.0e-3,
    f_tol::F = 1.0e-3,
    solver = BFGS()
)
```

逆転プロセスのためのパラメータを初期化します。

# 引数

  * `initial_conditions::Vector{F}`: 最適化のための出発点。
  * `lower_bound::Vector{F}`: 最適化変数の下限。
  * `upper_bound::Vector{F}`: 最適化変数の上限。
  * `regions_split::Vector{Int}`: 逆転プロセスのための高度と境界までの距離に基づいて地域分割の量を定義します。
  * `x_tol::F`: 変数収束の許容範囲。
  * `f_tol::F`: 関数値収束の許容範囲。
  * `solver`: 使用する最適化ソルバー。
