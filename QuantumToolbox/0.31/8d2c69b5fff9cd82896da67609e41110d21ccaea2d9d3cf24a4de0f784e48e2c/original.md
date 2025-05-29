```
permute(A::QuantumObject, order::Union{AbstractVector{Int},Tuple})
```

Permute the tensor structure of a [`QuantumObject`](@ref) `A` according to the specified `order` list

Note that this method currently works for [`Ket`](@ref), [`Bra`](@ref), and [`Operator`](@ref) types of [`QuantumObject`](@ref).

# Examples

If `order = [2, 1, 3]`, the Hilbert space structure will be re-arranged: $\mathcal{H}_1 \otimes \mathcal{H}_2 \otimes \mathcal{H}_3 \rightarrow \mathcal{H}_2 \otimes \mathcal{H}_1 \otimes \mathcal{H}_3$.

```jldoctest
julia> ψ1 = fock(2, 0);

julia> ψ2 = fock(3, 1);

julia> ψ3 = fock(4, 2);

julia> ψ_123 = tensor(ψ1, ψ2, ψ3);

julia> permute(ψ_123, (2, 1, 3)) ≈ tensor(ψ2, ψ1, ψ3)
true
```

!!! warning "Beware of type-stability!"
    It is highly recommended to use `permute(A, order)` with `order` as `Tuple` or `SVector` from [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl) to keep type stability. See the [related Section](@ref doc:Type-Stability) about type stability for more details.

