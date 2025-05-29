```
downsample(algorithm::MultiScaleAlgorithm, s::Int, x)
```

与えられた [`MultiScaleAlgorithm`](@ref) に従って、`x` をスケール `s` にダウンサンプリングおよび粗粒化します。戻り値の型は `algorithm` に依存します。
