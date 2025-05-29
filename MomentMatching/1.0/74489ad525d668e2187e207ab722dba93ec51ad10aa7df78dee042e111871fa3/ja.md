```julia
load_on_procs(mode::MomentMatching.EstimationMode)

```

すべてのプロセスにモデル固有のファイルをロードします。マルチプロセッシングでのみ使用されます。[`EstimationMode`](@ref) の任意のサブタイプに対して定義されるべきです。
