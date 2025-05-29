```
fock(N::Int, j::Int=0; dims::Union{Int,AbstractVector{Int},Tuple}=N, sparse::Union{Bool,Val}=Val(false))
```

次元 `N` のフォック状態 $\ket{\psi}$ を生成します。

異なるサブシステムが存在する場合は、次元のリスト `dims` を指定することも可能です。

!!! warning "型の安定性に注意してください！"
    型の安定性を保ちたい場合は、`fock(N, j, dims=dims, sparse=Val(sparse))` を使用することをお勧めします。`fock(N, j, dims=dims, sparse=sparse)` の代わりに使用してください。また、`Vector` の代わりに `Tuple` または [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl) の `SVector` を `dims` として使用することも検討してください。型の安定性に関する詳細については、[このリンク](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) と [関連セクション](@ref doc:Type-Stability) を参照してください。

