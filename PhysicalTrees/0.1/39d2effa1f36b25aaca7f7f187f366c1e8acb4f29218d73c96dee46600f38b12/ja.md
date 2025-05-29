```
init_octree(data, units, config::OctreeConfig, pids::Array{Int64,1})
```

データを前処理し（範囲を見つけ）、`pids` に空の木を設定し、マスタープロセスでインスタンスを返します。
