```julia
set_topology!(
    trajectory::Chemfiles.Trajectory,
    topology::Chemfiles.Topology
)

```

`trajectory`に関連付けられた`Topology`を設定します。このトポロジーは、ファイルの読み書き時に使用され、ファイル内のトポロジーを置き換えます。
