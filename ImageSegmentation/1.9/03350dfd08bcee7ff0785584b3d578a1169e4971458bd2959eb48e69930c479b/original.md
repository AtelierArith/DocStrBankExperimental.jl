```
edge = ImageEdge(index1, index2, weight)
```

Construct an edge in a Region Adjacency Graph. `index1` and `index2` are the integers corresponding to individual pixels/voxels (in the sense of linear indexing via `sub2ind`), and `weight` is the edge weight (measures the dissimilarity between pixels/voxels).
