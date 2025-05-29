```
init_gaussian_params(n::Int, N::Int, scale::Float64) -> GaussianParams
```

ランダムな中心と分散でガウスパラメータを初期化します。

# 引数

  * `n::Int`: ドメインの次元。
  * `N::Int`: ガウス関数の数。
  * `scale::Float64`: 分散のスケーリングファクター。

# 戻り値

  * `GaussianParams`: ガウス関数の中心、分散、および分布の符号付き和を作成するためのランダムなブールベクトルを含む構造体。

# 例

```julia
params = init*gaussian*params(3, 5, 2.0)
println(params.centers)  # ガウス関数の中心を出力
println(params.variances)  # ガウス関数の分散を出力
```
