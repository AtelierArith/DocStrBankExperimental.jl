```
MixtureDistribution(components, weights)
```

カスタム混合分布の実装で、以下のパラメータによってパラメータ化されています：

  * `C` 混合の型ファミリー
  * `CT` 重みの型

この実装は以下を解決します：

  * [Distributions.jl Issue 1669](https://github.com/JuliaStats/Distributions.jl/issues/1669)
  * [ReactiveMP.jl Issue 253](https://github.com/reactivebayes/ReactiveMP.jl/issues/253)
