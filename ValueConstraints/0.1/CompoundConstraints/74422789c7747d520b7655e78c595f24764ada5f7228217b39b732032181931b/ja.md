```julia
None(
    constraints::ValueConstraints.Interface.AbstractConstraint...
) -> ValueConstraints.BasicConstraints.Always

```

`constraints` のいずれも有効でないことを要求する複合制約、または言い換えれば、すべての `constraints` が無効であることを要求します。

これは、`0` の `constraints` が有効であることを要求する [`Exactly`](@ref) 制約をインスタンス化するための省略形です。

すべてのラップされた制約は「即座に」評価されます。つまり、`constraints` のいずれかが成功した場合でも、他のすべてが引き続き評価されます。
