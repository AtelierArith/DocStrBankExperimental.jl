```
 tvmeval(At::PeriodicTimeSeriesMatrix, t; method = "linear") -> A::Vector{Matrix}
```

周期的な時系列行列の時間応答を評価します。

周期的な時系列行列 `At` と時間値のベクトル `t` に対して、各時間値 `t[i]` に対して補間/外挿に基づく近似 `A[i]` が評価されます。キーワードパラメータ `method` は、周期的データに使用される補間/外挿方法を指定します。以下の補間方法が [`Interpolations.jl`](https://github.com/JuliaMath/Interpolations.jl) パッケージから選択できます：

`method = "constant"` - 次元0の周期的Bスプラインを使用；

`method = "linear"` - 次元1の周期的Bスプラインを使用（周期的線形補間）（デフォルト）；

`method = "quadratic"` - 次元2の周期的Bスプラインを使用（周期的二次補間）；

`method = "cubic"` - 次元3の周期的Bスプラインを使用（周期的三次補間）。
