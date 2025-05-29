```
distance(t1::Tree, t2::Tree; type = :RF, normalize = false)
```

Compute distance between two trees. See `TreeTools.tree_distance_types` for allowed types. If `normalize`, the distance is normalized to `[0,1]`.
