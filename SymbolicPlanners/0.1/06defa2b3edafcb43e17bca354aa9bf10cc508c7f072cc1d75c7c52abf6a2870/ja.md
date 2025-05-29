```
EpsilonMixturePolicy(domain, policy, epsilons, [weights, rng::AbstractRNG])
```

異なる `epsilons` と混合 `weights` を持つε-greedyポリシーの混合です。指定は `Vector` として行います。提供される場合、`weights` は非負であり、合計が1でなければなりません。そうでない場合は、均一な混合が仮定されます。`domain` は各状態で利用可能なアクションを決定するために必要です。
