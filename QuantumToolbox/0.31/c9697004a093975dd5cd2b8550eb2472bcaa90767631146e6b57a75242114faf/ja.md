```
basis(N::Int, j::Int = 0; dims::Union{Int,AbstractVector{Int},Tuple}=N)
```

[`fock`](@ref)のようなフォック状態を生成します。

異なるサブシステムが存在する場合は、次元のリスト`dims`を指定することも可能です。

!!! warning "型の安定性に注意!"
    型の安定性を保ちたい場合は、`Vector`の代わりに`Tuple`または[StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl)の`SVector`として`dims`を指定して`basis(N, j, dims=dims)`を使用することをお勧めします。型の安定性に関する詳細については、[このリンク](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type)および[関連セクション](@ref doc:Type-Stability)を参照してください。

