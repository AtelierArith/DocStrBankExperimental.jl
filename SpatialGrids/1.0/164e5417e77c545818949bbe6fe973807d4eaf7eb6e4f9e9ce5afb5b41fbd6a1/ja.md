```
in_cuboid(grid::SparseVoxelGrid, voxel::Voxel, radius::Int)
in_cuboid(grid::SparseVoxelGrid, voxel_id::NTuple{3,Int}, radius::Int)
```

参照ボクセルまたはボクセルIDの周囲の`radius`内に隣接するボクセルを検索します。各イテレーションで`Voxel`を返します。

### 例

`in_cuboid`関数は`do`ブロック構文を使用して実装できます：

```julia
radius = 1
query_voxel = (1,1,1)
in_cuboid(grid, query_voxel, radius) do voxel
    for index in voxel
        # point[:, index]で何かを行う
    end
    # または、すべてのインデックスを配列に収集する
    indices = collect(voxel)
end
```

あるいは、各イテレーションでボクセルを返す`for`ループを使用することもできます：

```julia
for voxel in in_cuboid(grid, query_voxel, radius)
    # `Voxel`で何かを行う（つまり、collect(voxel)やfor index in voxelなど）
end
```
