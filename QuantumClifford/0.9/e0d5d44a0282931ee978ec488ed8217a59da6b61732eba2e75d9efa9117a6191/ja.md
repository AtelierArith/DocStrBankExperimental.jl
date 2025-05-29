与えられた演算子のセットから、同じ表形式だが異なる位相を持つすべての演算子を返します。

```jldoctest
julia> length(collect(enumerate_phases(enumerate_cliffords(2))))
11520
```

参照: [`enumerate_cliffords`](@ref), [`clifford_cardinality`](@ref)。
