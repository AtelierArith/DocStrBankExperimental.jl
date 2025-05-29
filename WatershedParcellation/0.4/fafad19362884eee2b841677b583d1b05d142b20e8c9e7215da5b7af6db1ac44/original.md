```
run_watershed(metric, minima, neighbors)
```

Run the watershed algorithm on `metric`, using its `minima` (as returned from  `find_minima()`) as initialization points and guided by the topology given in the adjacency list `neighbors`.

Some optional parameters can be tuned:

  * `nsteps`: the number of bins into which to discretize the heights (default 400)
  * `fracmaxh`: a scaling factor to determine a ceiling on height values (default 1.0)
