```
GP = partition_tree_fiedler(G::GraphSig; method::Symbol = :Lrw, swapRegion::Bool = true)
```

Generate a partition tree for a graph using the Fiedler vector of either  L (the unnormalized Laplacian) or L_rw (the random-walk normalized  Laplacian).

### Input ArgumenInt

  * `G::GraphSig`: an input GraphSig object
  * `method::Symbol`: how the partition tree was constructed (default: :Lrw)
  * `swapRegion::Bool`: swap the child regions based on the sum of the subgraphs' edge weights (default: true)

### Output Argument

  * `GP::GraphPart`: an ouput GraphPart object

Copyright 2015 The RegenInt of the University of California

Implemented by Jeff Irion (Adviser: Dr. Naoki Saito) | Translated and modified by Naoki Saito, Feb. 7, 2017
