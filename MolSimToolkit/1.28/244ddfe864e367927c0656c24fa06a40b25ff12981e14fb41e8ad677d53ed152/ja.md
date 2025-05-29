```
FramePositions{T,P<:Point3D{T},M<:AbstractArray{T}} <: AbstractVector{P}
```

原子のセットの位置を格納するコンテナです。位置は行列に格納されており、各列は原子の座標に対応しています。このコンテナは、`Chemfiles.Frame` からの座標をユーザーに透過的に使用できるように設計されており、座標は `p[i]` としてアクセスできます。ここで `i` は原子のインデックスです。

原子の座標には `p[i].x`、`p[i].y`、および `p[i].z` でアクセスできます。

`FramePositions` オブジェクトは `positions` 関数を使用して作成できます。`FramePositions` での構築は公開APIの一部とは見なされません。

# 例

```julia-repl # to be doctest
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> frame = current_frame(simulation);

julia> p = positions(frame)
20465-element FramePositions{Float64, Point3D{Float64}, Chemfiles.ChemfilesArray}:
 [5.912472724914551, 10.768872261047363, 28.277008056640625]
 [5.040304183959961, 10.810898780822754, 27.71207046508789]
 ⋮
 [11.16289234161377, -37.30374526977539, 22.80788230895996]

julia> p[1]
3-element Point3D{Float64} with indices SOneTo(3):
  5.912472724914551
 10.768872261047363
 28.277008056640625

julia> p[1].x
5.912472724914551

julia> p[1].y
10.768872261047363

julia> p[1].z
28.277008056640625
```

位置のスライスやビューを取得することも可能です：

```
julia> p[1:2]
2-element FramePositions{Float64, Point3D{Float64}, Matrix{Float64}}:
 [5.912472724914551, 10.768872261047363, 28.277008056640625]
 [5.040304183959961, 10.810898780822754, 27.71207046508789]

julia> @view(coor[1:2])
 2-element FramePositions{Float64, Point3D{Float64}, SubArray{Float64, 2, Chemfiles.ChemfilesArray, Tuple{Base.Slice{Base.OneTo{Int64}}, UnitRange{Int64}}, false}}:
  [5.912472724914551, 10.768872261047363, 28.277008056640625]
  [5.040304183959961, 10.810898780822754, 27.71207046508789]
 
```
