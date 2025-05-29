```
NamedTupleDist <: MultivariateDistribution
NamedTupleDist <: MultivariateDistribution
```

`NamedTuple`型の変数を持つ分布です。

`NamedTupleDist`は、名前付き変数/パラメータのセットにおける各変数/パラメータの分布を指定するための効果的なメカニズムを提供します。

`NamedTupleDist`に対して`varshape`を呼び出すと、[`NamedTupleShape`](@ref)が得られます。
