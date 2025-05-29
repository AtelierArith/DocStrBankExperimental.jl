```
generate_conditional_samples(model, rule::Flux.Optimise.AbstractOptimiser, n::Int, y::Int; kwargs...)
```

与えられたモデル、サンプラー、およびサンプリングルールの条件付きサンプルを生成するための便利な関数です。`n`が`missing`の場合、サンプラーの`batch_size`が使用されます。条件付けの値`y`を指定する必要があります。
