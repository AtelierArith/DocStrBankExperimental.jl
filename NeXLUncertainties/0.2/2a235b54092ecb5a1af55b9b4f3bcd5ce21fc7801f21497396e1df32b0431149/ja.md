```
mcpropagate(mm::MeasurementModel, inputs::UncertainValues, n::Int, parallel::Bool=true, rng::AbstractRNG = Random.GLOBAL_RNG)::UncertainValues
```

`inputs`を`MeasurementModel`を通じてモンテカルロアルゴリズムを使用して伝播させます。このとき、`inputs`は共分散が`inputs`からの`MvNormal`分布で表されると仮定されます。'n'回の反復を行い、`parallel=true`の場合はマルチスレッド処理を行います。
