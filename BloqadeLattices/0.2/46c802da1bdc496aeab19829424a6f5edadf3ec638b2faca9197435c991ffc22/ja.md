```
make_kdtree(atoms::AtomList{D,T}) where {T, D}
```

入力 `atoms` からパッケージ [NearestNeighbors](https://github.com/KristofferC/NearestNeighbors.jl) で定義された `KDTree` インスタンスを返します。
