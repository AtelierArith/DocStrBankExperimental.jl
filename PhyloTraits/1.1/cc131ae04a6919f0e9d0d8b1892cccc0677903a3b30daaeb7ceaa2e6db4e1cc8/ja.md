`BinaryTraitSubstitutionModel`の場合、これは2です：

```jldoctest
julia> m1 = BinaryTraitSubstitutionModel([1.0,2.0], ["low","high"])
Binary Trait Substitution Model:
rate low→high α=1.0
rate high→low β=2.0

julia> nstates(m1)
2
```
