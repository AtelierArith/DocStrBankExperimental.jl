```
TreeSA{RT,IT,GM}
TreeSA(; sc_target=20, βs=collect(0.01:0.05:15), ntrials=10, niters=50,
    sc_weight=1.0, rw_weight=0.2, initializer=:greedy, greedy_config=GreedyMethod(; nrepeat=1))
```

Optimize the einsum contraction pattern using the simulated annealing on tensor expression tree.

  * `sc_target` is the target space complexity,
  * `ntrials`, `βs` and `niters` are annealing parameters, doing `ntrials` indepedent annealings, each has inverse tempteratures specified by `βs`, in each temperature, do `niters` updates of the tree.
  * `sc_weight` is the relative importance factor of space complexity in the loss compared with the time complexity.
  * `rw_weight` is the relative importance factor of memory read and write in the loss compared with the time complexity.
  * `initializer` specifies how to determine the initial configuration, it can be `:greedy` or `:random`. If it is using `:greedy` method to generate the initial configuration, it also uses two extra arguments `greedy_method` and `greedy_nrepeat`.
  * `nslices` is the number of sliced legs, default is 0.
  * `fixed_slices` is a vector of sliced legs, default is `[]`.

### References

  * [Recursive Multi-Tensor Contraction for XEB Verification of Quantum Circuits](https://arxiv.org/abs/2108.05665)
