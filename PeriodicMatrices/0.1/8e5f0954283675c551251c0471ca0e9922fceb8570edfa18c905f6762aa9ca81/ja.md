```
 ts2pfm(At::PeriodicTimeSeriesMatrix; method = "linear") -> A::PeriodicFunctionMatrix
```

補間された周期的時間系列行列に対応する周期関数行列を計算します。与えられた周期的時間系列行列 `At` に対して、周期関数行列 `A(t)` は、`A(t) = t -> etpf(t)` というマッピングとして定義され、ここで `etpf(t)` は [`Interpolations.jl`](https://github.com/JuliaMath/Interpolations.jl) パッケージで提供される周期的補間/外挿オブジェクトです。キーワードパラメータ `method` は、使用する補間/外挿方法を次のように指定します：

`method = "constant"` - 次元0の周期的Bスプラインを使用（周期的定数補間）;

`method = "linear"` - 次元1の周期的Bスプラインを使用（周期的線形補間）（デフォルト）;

`method = "quadratic"` - 次元2の周期的Bスプラインを使用（周期的二次補間）;

`method = "cubic"` - 次元3の周期的Bスプラインを使用（周期的三次補間）。
