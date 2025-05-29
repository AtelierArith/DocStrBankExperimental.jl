```
pathwidth(g::AbstractGraph, method)
```

Compute the optimal path decomposition of graph `g`, returns a `Layout` instance. `method` can be

```
* Greedy(; nrepeat=10)
* MinhThiTrick
```
