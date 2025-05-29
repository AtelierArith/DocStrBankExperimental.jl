```
label_propagation(g, maxiter=1000; rng=nothing, seed=nothing)
```

Community detection using the label propagation algorithm. Return two vectors: the first is the label number assigned to each node, and the second is the convergence history for each node. Will return after `maxiter` iterations if convergence has not completed.

### References

  * [Raghavan et al.](http://arxiv.org/abs/0709.2938)
