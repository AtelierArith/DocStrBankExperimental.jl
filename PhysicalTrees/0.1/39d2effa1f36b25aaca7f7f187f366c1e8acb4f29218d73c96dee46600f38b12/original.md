```
init_octree(data, units, config::OctreeConfig, pids::Array{Int64,1})
```

Preprocess data (find the extent), set up empty trees on `pids`, and return the instance on master process.
