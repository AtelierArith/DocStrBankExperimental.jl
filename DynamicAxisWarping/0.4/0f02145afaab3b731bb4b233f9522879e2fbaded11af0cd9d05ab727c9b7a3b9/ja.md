```
dbaclust(
    sequences,
    nclust::Int,
    dtwdist::DTWDistance;
    n_init::Int           = 1,
    iterations::Int       = 100,
    inner_iterations::Int = 10,
    rtol::Float64         = 1e-4,
    rtol_inner::Float64   = rtol,
    threaded::Bool        = false,
    show_progress::Bool   = true,
    store_trace::Bool     = true,
    i2min::AbstractVector = [],
    i2max::AbstractVector = [],
)
```

# 引数:

  * `nclust`: クラスタの数
  * `n_init`: 初期化の試行回数
  * `inner_iterations`: 内部アルゴリズムの反復回数
  * `i2min`: ワーピングパスの境界
  * `threaded`: マルチスレッドを使用する
