```
run_sampler!(rng::AbstractRNG, sampler::RejectionSampler, n::Int)
run_sampler!(sampler::RejectionSampler, n::Int)
```

これは、`sampler`の目的関数の`n`個の独立同分布サンプルを引き出し、各イテレーションで新しいセグメントをそのエンベロープに追加することによって`sampler`のエンベロープを適応させます。
