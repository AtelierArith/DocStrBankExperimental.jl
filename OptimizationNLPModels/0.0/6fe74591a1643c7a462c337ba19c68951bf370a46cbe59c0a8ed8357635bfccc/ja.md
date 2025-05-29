```
OptimizationFunction(nlpmodel::AbstractNLPModel, adtype::AbstractADType = NoAD())
```

`nlpmodel`で定義された`NLPModel`から`OptimizationFunction`を返します。利用可能な導関数はモデルから再利用され、残りは`adtype`で指定された自動微分バックエンドで補完されます。
