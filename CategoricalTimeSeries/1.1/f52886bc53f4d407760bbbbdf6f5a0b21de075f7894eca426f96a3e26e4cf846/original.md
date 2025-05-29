```
search_optima!(m::IB, n_iter = 10000)
```

The original IB algorithm can converge to a local optima. To find the global optima, search*optima! performs 'n*iter' optimization of input model 'm', randomly re-initializing it at every iteration. The best optimization is kept and 'm' is modified in-place.
