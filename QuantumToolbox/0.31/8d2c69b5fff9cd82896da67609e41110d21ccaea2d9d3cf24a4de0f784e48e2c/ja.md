```
permute(A::QuantumObject, order::Union{AbstractVector{Int},Tuple})
```

指定された `order` リストに従って [`QuantumObject`](@ref) `A` のテンソル構造を置換します。

このメソッドは現在、[`Ket`](@ref)、[`Bra`](@ref)、および [`Operator`](@ref) タイプの [`QuantumObject`](@ref) に対して機能します。

# 例

`order = [2, 1, 3]` の場合、ヒルベルト空間の構造は再配置されます: $\mathcal{H}_1 \otimes \mathcal{H}_2 \otimes \mathcal{H}_3 \rightarrow \mathcal{H}_2 \otimes \mathcal{H}_1 \otimes \mathcal{H}_3$。

```jldoctest
julia> ψ1 = fock(2, 0);

julia> ψ2 = fock(3, 1);

julia> ψ3 = fock(4, 2);

julia> ψ_123 = tensor(ψ1, ψ2, ψ3);

julia> permute(ψ_123, (2, 1, 3)) ≈ tensor(ψ2, ψ1, ψ3)
true
```

!!! warning "型の安定性に注意してください！"
    型の安定性を保つために、`order` を `Tuple` または [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl) の `SVector` として `permute(A, order)` を使用することを強くお勧めします。型の安定性に関する詳細は、[関連セクション](@ref doc:Type-Stability)を参照してください。

