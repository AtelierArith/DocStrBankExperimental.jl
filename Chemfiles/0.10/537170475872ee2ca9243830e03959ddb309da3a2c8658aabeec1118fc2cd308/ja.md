```julia
dihedrals(topology::Chemfiles.Topology) -> Matrix{UInt64}

```

`topology`内の二面角を取得し、`4 x dihedrals_count(topology)`の配列にします。
