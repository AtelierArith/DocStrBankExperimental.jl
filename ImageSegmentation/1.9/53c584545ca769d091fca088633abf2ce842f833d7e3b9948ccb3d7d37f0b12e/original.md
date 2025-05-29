```
index_map, num_segments = felzenszwalb(edges, num_vertices, k, min_size=0)
```

Segment an image represented as Region Adjacency Graph(RAG) using Felzenszwalb's segmentation algorithm. Each pixel/region corresponds to a node in the graph and weights on each edge measure the dissimilarity between pixels. The function returns the number of segments and index mapping from nodes of the RAG to segments.

Parameters:

  * `edges`:        Array of edges in RAG. Each edge is represented as `ImageEdge`.
  * `num_vertices`: Number of vertices in RAG
  * `k`:            Threshold for region merging step. Larger threshold will result in bigger segments.
  * `min_size`:     Minimum segment size (in # pixels)
