```julia
bonds(topology::Chemfiles.Topology) -> Matrix{UInt64}

```

`topology`の結合を取得し、`2 x bonds_count(topology)`配列にします。
