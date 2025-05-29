```
reservoir_sample(rng, iter, [wv]; method = :alg_L)
reservoir_sample(rng, iter, [wv], n; replace = false, ordered = false, kwargs...)
```

置換ありおよび置換なしのリザーバサンプリングアルゴリズム。

オプションの `kwargs` は、関数によって内部的に呼び出されるより具体的なメソッドに渡されます。これらは次のいずれかです。

  * [`reservoir_sample_without_replacement`](@ref)
  * [`reservoir_sample_with_replacement`](@ref)
  * [`weighted_reservoir_sample_without_replacement`](@ref)
  * [`weighted_reservoir_sample_with_replacement`](@ref)

実行されるサンプリングの種類に応じて。
