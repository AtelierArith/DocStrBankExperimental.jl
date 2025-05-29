与えられた演算子に対して、同じタブローを持つが異なる位相を持つすべての演算子を返します。

```jldoctest
julia> length(collect(enumerate_phases(tCNOT)))
16
```

参照: [`enumerate_cliffords`](@ref), [`clifford_cardinality`](@ref)。
