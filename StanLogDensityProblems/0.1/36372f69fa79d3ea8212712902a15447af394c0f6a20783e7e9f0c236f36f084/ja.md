```
StanProblem(lib::String[, data::String[ seed::Int]]; nan_on_error::Bool=false, kwargs...)
```

[`BridgeStan.StanModel`](@extref)を構築し、それを`StanProblem`としてラップします。

`lib`は、コンパイルされたStanモデルへのパスまたは`.stan`ファイルへのパスです。引数の詳細については、[`BridgeStan.StanModel`](@extref)のドキュメント文字列を参照してください。

!!! note
    デフォルトでは、Stanはマルチスレッドサポートでモデルをコンパイルしません。これが必要な場合は、`make_args=["STAN_THREADS=true"]`を`kwargs`に渡してください。

