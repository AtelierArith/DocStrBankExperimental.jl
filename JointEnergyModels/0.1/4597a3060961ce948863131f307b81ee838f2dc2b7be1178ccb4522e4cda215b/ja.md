```
generate_samples(jem::JointEnergyModel, n::Int; kwargs...)
```

特定のエネルギーモデルのサンプルを生成するための便利な関数です。`n`が`missing`の場合、サンプラーの`batch_size`が使用されます。
