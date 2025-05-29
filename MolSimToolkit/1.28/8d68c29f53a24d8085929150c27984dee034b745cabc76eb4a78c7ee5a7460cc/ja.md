```
positions(frame::Chemfiles.Frame)
```

`Chemfiles.Frame`内の原子の位置を`FramePositions`オブジェクトとして返します。

これはシミュレーション内の原子の位置にアクセスするためのデフォルトの方法です。

# 例

```julia-repl # to be doctest
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> frame = current_frame(simulation);

julia> p = positions(frame);

julia> p[1].x 
5.912472724914551

```
