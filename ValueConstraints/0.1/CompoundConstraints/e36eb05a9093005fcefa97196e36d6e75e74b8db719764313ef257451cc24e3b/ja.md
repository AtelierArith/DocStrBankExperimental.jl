```julia
struct AtLeast{S, T<:Tuple{ValueConstraints.Interface.AbstractConstraint, Vararg{ValueConstraints.Interface.AbstractConstraint}}} <: ValueConstraints.CompoundConstraints.CompoundConstraint
```

  * `constraints::Tuple{ValueConstraints.Interface.AbstractConstraint, Vararg{ValueConstraints.Interface.AbstractConstraint}}`: 評価される `AbstractConstraint` のコレクション。

ラップされた `constraints` のうち少なくとも `S` が有効であることを要求する複合制約。

すべてのラップされた `constraints` は「即時に」評価されます。つまり、すでに十分な数の `constraints` が成功していても、他のすべてがまだ評価されます。
