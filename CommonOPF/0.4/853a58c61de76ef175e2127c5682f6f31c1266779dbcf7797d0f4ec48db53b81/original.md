```
check_paths_for_loads(paths::AbstractVecOrMat, net::Network)
```

paths is vector of vectors containing bus names for parallel lines. if any load busses are in the paths then an error is thrown because we are not handling that case yet.
