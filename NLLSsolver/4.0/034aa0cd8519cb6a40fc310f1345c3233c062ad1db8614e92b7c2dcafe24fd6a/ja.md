```
NLLSsolver.varindices(mycost)
```

`mycost`が依存する変数のインデックスを表す静的ベクターを返します。

# 例

最初と3番目の変数に依存する`MyCost <: AbstractCost`型のコストの場合、ユーザーは次の関数を定義する必要があります。

```julia
    NLLSsolver.varindices(::MyCost) = SVector(1, 3)
```

!!! note
    必要なユーザー専門のAPI関数。

