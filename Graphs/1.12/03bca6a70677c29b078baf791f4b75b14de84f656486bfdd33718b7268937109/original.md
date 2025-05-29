```
normalized_cut(g, thres, distmx=weights(g), [num_cuts=10]);
```

Perform [recursive two-way normalized graph-cut](https://en.wikipedia.org/wiki/Segmentation-based_object_categorization#Normalized_cuts) on a graph, partitioning the vertices into disjoint sets. Return a vector that contains the set index for each vertex.

It is important to identify a good threshold for your application. A bisection search over the range (0,1) will help determine a good value of thres.

### Keyword Arguments

  * `thres`: Subgraphs aren't split if best normalized cut is above this threshold
  * `num_cuts`: Number of cuts performed to determine optimal cut

### References

"Normalized Cuts and Image Segmentation" - Jianbo Shi and Jitendra Malik
