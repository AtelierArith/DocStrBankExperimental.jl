```julia
numalocal() -> NUMA.NUMALocal

```

ローカルNUMAノードを表す配列初期化子を返します。例えば、`Vector{Float64}(numalocal(), 1024)`のように使用します。
