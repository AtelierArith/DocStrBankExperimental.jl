```julia
struct AtMost{S, T<:Tuple{ValueConstraints.Interface.AbstractConstraint, Vararg{ValueConstraints.Interface.AbstractConstraint}}} <: ValueConstraints.CompoundConstraints.CompoundConstraint
```

  * `constraints::Tuple{ValueConstraints.Interface.AbstractConstraint, Vararg{ValueConstraints.Interface.AbstractConstraint}}`: 評価される `AbstractConstraint` のコレクション。

ラップされた `constraints` のうち、最大で `S` までが有効であることを要求する複合制約。

すべてのラップされた `constraints` は「即座に」評価されます。つまり、すでに成功した `constraints` が多すぎる場合でも、他のすべてがまだ評価されます。
