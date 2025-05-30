```
cpdag(skel::DiGraph)
```

Computes CPDAG from a DAG using Chickering's conversion algorithm  (equivalent to the PC algorithm with `d`-seperation as independence test, see `pc_oracle`.)

Reference: M. Chickering: Learning equivalence classes of Bayesian network structures. Journal of Machine Learning Research 2 (2002). M. Chickering: A Transformational Characterization of Equivalent Bayesian Network Structures. (1995).

Note that the edge order defined there is already partly encoded into the representation of a DiGraph.
