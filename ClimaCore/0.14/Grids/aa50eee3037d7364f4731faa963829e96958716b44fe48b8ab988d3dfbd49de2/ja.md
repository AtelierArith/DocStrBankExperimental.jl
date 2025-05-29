```
FiniteDifferenceGrid(topology::Topologies.IntervalTopology)
FiniteDifferenceGrid(device::ClimaComms.AbstractDevice, mesh::Meshes.IntervalMesh)
```

`IntervalTopology`（または`IntervalMesh`）から`FiniteDifferenceGrid`を構築します。

これは、必要なすべての幾何学的情報を含むオブジェクトです。

不必要な重複を避けるために、グリッドの構築をメモ化します。
