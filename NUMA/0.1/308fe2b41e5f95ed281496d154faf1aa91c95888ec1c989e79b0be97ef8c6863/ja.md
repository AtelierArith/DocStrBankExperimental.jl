```julia
numanode(i::Integer) -> NUMA.NUMANode

```

特定のNUMAノードを表す配列初期化子を返します。例えば、`Vector{Float64}(numanode(1), 1024)`のように使用します。
