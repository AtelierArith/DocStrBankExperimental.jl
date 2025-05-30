```
alt_cpdag(g::DiGraph)
```

Computes CPDAG from a DAG using a simpler adaption of Chickering's conversion algorithm without ordering all edges (equivalent to the PC algorithm with `d`-separation as independence test, see `pc_oracle`.)

Reference: M. Chickering: Learning equivalence classes of Bayesian network structures. Journal of Machine Learning Research 2 (2002). M. Chickering: A Transformational Characterization of Equivalent Bayesian Network Structures. (1995).
