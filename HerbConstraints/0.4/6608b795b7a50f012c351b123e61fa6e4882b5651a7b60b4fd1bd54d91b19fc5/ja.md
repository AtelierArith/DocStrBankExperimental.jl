```
StateHole <: AbstractUniformHole
```

`StateHole`は`UniformSolver`によって使用される均一なホールです。ドメインの操作は逆伝播のために追跡されます。

  * `domain`: このホールが取ることができるルールノードを表す`StateSparseSet`。もしsize(domain) == 1であれば、このホールは`RuleNode`のように振る舞うべきです。
  * `children`: 式木におけるこのホールの子供たち。
