```
fock_dm(N::Int, j::Int=0; dims::Union{Int,AbstractVector{Int},Tuple}=N, sparse::Union{Bool,Val}=Val(false))
```

フォック状態の密度行列表現。

[`fock`](@ref) の外積を介して構築されます。

!!! warning "型の安定性に注意してください！"
    型の安定性を保ちたい場合は、`fock_dm(N, j, dims=dims, sparse=Val(sparse))` を使用することをお勧めします。`fock_dm(N, j, dims=dims, sparse=sparse)` の代わりに。`dims` を `Vector` の代わりに `Tuple` または [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl) の `SVector` として使用することも検討してください。型の安定性に関する詳細については、[このリンク](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) と [関連セクション](@ref doc:Type-Stability) を参照してください。

