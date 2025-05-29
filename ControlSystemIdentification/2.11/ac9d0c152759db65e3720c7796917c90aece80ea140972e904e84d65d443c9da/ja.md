```
tfest(data::FRD, basis::AbstractStateSpace; 
    freq_weight = 1 ./ (data.w .+ data.w[2]),
    opt = BFGS(),
    metric::M = abs2,
    opts = Optim.Options(
        store_trace       = true,
        show_trace        = true,
        show_every        = 50,
        iterations        = 1000000,
        allow_f_increases = false,
        time_limit        = 100,
        x_tol             = 1e-5,
        f_tol             = 0,
        g_tol             = 1e-8,
        f_calls_limit     = 0,
        g_calls_limit     = 0,
)
```

周波数領域データにパラメトリック伝達関数を適合させるために、事前に指定された基底を使用します。

# 引数:

  * `data`: 周波数領域データを持つ `FRD` オブジェクト。

function kautz(a::AbstractVector)

  * `basis`: 推定のための基底。例えば、`laguerre, laguerre_oo, kautz` を参照してください。
  * `freq_weight`: 周波数ごとの重みのベクトル。デフォルトはおおよそ `1/f` です。
  * `opt`: 使用するOptim最適化器。
  * `opts`: ソルバーオプションを制御する `Optim.Options`。
