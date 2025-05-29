```
abstract type RBSpace <: FESpace end
```

`FESpace`のベクトル部分空間を表します。

サブタイプ:

  * [`SingleFieldRBSpace`](@ref)
  * [`MultiFieldRBSpace`](@ref)
  * [`EvalRBSpace`](@ref)
