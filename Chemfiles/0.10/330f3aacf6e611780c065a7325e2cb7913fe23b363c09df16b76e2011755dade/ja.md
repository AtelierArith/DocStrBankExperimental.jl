```julia
angles(topology::Chemfiles.Topology) -> Matrix{UInt64}

```

`topology`の角度を取得し、`3 x angles_count(topology)`の配列にします。
