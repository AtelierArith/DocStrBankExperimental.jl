```
nullmodel(::Type{C}, N::SpeciesInteractionNetwork{<:Partiteness{T}, <:Binary}, sp::T) where {C <: PermutationConstraint, T}
```

種 `sp` の相互作用確率が、最初の引数として与えられた置換制約によって指定されたヌルモデルの下で与えられた確率に置き換えられた確率的ネットワークを返します; [`nullmodel`](@ref) を参照してください。種 `sp` に関与しないすべての相互作用は、その確率が1に設定されます。

元の出版物 [Saavedra2011Strong](@cite) は、置換制約として [`Degree`] を使用していますが、この関数はより一般的に書かれています。

このネットワークは [`speciescontribution`](@ref) に渡すことができます。

###### 参考文献

[Saavedra2011Strong](@citet*)
