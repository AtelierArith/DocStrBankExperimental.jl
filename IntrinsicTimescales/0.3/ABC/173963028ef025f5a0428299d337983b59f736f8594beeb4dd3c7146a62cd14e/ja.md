```
find_MAP(theta_accepted::Matrix{Float64}, N::Int)
```

グリッドサーチを用いて事後分布からMAP推定値を求めます。

# 引数

  * `theta_accepted::Matrix{Float64}`: ABCの最終ステップからの受け入れられたサンプルの行列
  * `N::Int`: グリッドサーチのためのサンプル数

# 戻り値

  * `theta_map::Vector{Float64}`: パラメータのMAP推定値
