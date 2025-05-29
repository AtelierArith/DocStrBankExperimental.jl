```
maxsimplecycles(dg::::IsDirected, byscc::Bool = true)
```

Compute the theoretical maximum number of cycles in the directed graph `dg`.

The computation can be performed assuming the graph is complete or taking into account the decomposition in strongly connected components (`byscc` parameter).

### Performance

A more efficient version is possible.

### References

  * [Johnson](http://epubs.siam.org/doi/abs/10.1137/0204007)
