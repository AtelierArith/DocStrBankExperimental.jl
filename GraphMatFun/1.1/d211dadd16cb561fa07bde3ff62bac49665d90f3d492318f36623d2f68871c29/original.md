```
    (graph,cref)=graph_denman_beavers(k;T=ComplexF64,cref_mode=0)
```

Creates the graph corresponding to the Denman–Beavers iteration for the matrix square root, using k iterations. The kwarg `cref_mode` specifies if references to all X and Y (`cref_mode=0`) should be stored or just Y (`cref_mode=-1`) or just X (`cref_mode=1`).

**Reference**

1. E. Denman and A. Beavers. "The matrix sign function and computations in systems". Applied Mathematics and Computation, 2(1), 1976. DOI: [10.1016/0096-3003(76)90020-5](https://doi.org/10.1016/0096-3003(76)90020-5)
