```
query(tree::STRtree, extent::Extent)
query(tree::STRtree, geom)
```

Query the tree for geometries whose extent intersects with the given extent or the extent of the given geometry. Returns a vector of indices of the geometries that can be used to index into the original collection of geometries under the assumption that the collection has not been modified since the tree was built.
