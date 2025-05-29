```
SparseVoxelGrid(points, voxel_size)
SparseVoxelGrid(points, voxel_size::NTuple{3, AbstractFloat})
```

3Dポイントをボクセルに整理することによって、スパース空間グリッドを作成します。`points`は3xN行列または`PointCloud`であることができます。`voxel_size`は各軸で均一なサイズのボクセルを作成するか、3Dタプルであれば各軸のサイズを指定できます。

### 例

任意のポイントに対してボクセルの辺の長さが10メートルの空間グリッドを作成するには：

```julia
using PointClouds
points = rand(3, 100000) * 20.0
grid = SparseVoxelGrid(points, 10.0)
```

作成されたグリッドは反復可能なオブジェクトであり、各反復で`Voxel`を返します。各ボクセルには`for`ループで直接アクセスすることができ、すべてのボクセルを配列に`collect`することもできます。同様に、返された`Voxel`は点のインデックスを返す反復可能なオブジェクトです：

```julia
# グリッド内の各ボクセルを反復処理
for voxel in grid
    # ボクセル内の各点のインデックスを取得
    for idx in voxel
        # points[:,idx]で処理を行う
    end
    # または、ボクセル内のすべての点のインデックスを取得したい場合
    all_point_indices = collect(voxel)
end
```
