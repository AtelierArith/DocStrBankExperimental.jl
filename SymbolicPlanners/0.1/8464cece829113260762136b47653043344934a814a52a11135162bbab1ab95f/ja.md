```
BoltzmannMixturePolicy(policy, temperatures, [weights, rng::AbstractRNG])
```

異なる `temperatures` と混合 `weights` を持つボルツマンポリシーの混合です。指定された場合、`weights` は非負であり、合計が1でなければなりません。そうでない場合は、均一な混合が仮定されます。Q値は、コンストラクタに引数として提供された基礎となる `policy` に従って計算されます。
