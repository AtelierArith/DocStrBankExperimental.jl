```
OptimizationProblem(nlpmodel::AbstractNLPModel, adtype::AbstractADType = NoAD())
```

`nlpmodel`で定義された境界と制約を持つ`OptimizationProblem`を返します。最適化関数とその導関数は、利用可能な場合は`nlpmodel`から再利用され、指定された`adtype`によって自動微分バックエンドで補完されます。
