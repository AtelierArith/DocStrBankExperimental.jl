```
MixturePolicy(policies, [weights, rng::AbstractRNG])
```

関連する `weights` を持つ基礎となる `policies` の混合。提供される場合、`weights` は非負であり、合計が1でなければなりません。そうでない場合は、均一な混合が仮定されます。
