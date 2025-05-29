```julia
add_residue!(
    topology::Chemfiles.Topology,
    residue::Chemfiles.Residue
)

```

この`topology`に`residue`のコピーを追加します。

残留物のIDは、トポロジーにすでに存在していてはいけません。また、残留物は他の残留物にすでに存在しない原子のみを含む必要があります。
