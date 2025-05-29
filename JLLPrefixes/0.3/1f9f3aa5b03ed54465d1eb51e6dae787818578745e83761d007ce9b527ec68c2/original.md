```
collect_artifact_paths(dependencies::Vector;
                       platform = HostPlatform(),
                       verbose = false)
```

A convenience wrapper around `collect_artifact_metas()` that will peel the `meta` objects, walk the dependency tree, and return a dictionary mapping each package in `dependencies` to a flattened vector of artifact path directories.  Use `flatten_artifact_paths()` to further flatten the tree into just a single vector.
