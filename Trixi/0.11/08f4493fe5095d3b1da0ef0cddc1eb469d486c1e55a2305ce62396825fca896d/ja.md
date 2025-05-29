```
UnstructuredMesh2D <: AbstractMesh{2}
```

非構造（曲がっている可能性のある）四角形メッシュ。

```
UnstructuredMesh2D(filename; RealT=Float64, periodicity=false)
```

すべてのメッシュ情報、隣接結合、および境界曲線情報は、メッシュファイル `filename` から読み込まれます。
