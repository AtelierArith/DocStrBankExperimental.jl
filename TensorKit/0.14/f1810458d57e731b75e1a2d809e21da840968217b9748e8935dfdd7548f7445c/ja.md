```
struct BraidingTensor{T,S<:IndexSpace} <: AbstractTensorMap{T, S, 2, 2}
BraidingTensor(V1::S, V2::S, adjoint::Bool=false) where {S<:IndexSpace}
```

特定の[`AbstractTensorMap`](@ref)のサブタイプで、最初の入力を2番目の入力の上に編むブレーディングテンソルを表します。その逆は随伴として得られます。

`domain(BraidingTensor(V1, V2)) == V1 ⊗ V2` および `codomain(BraidingTensor(V1, V2)) == V2 ⊗ V1` が成り立ちます。
