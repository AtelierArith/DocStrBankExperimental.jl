```
SABipartite{RT,BT}
SABipartite(; sc_target=25, ntrials=50, βs=0.1:0.2:15.0, niters=1000
    max_group_size=40, greedy_config=GreedyMethod(), initializer=:random)
```

Optimize the einsum code contraction order using the Simulated Annealing bipartition + Greedy approach. This program first recursively cuts the tensors into several groups using simulated annealing, with maximum group size specifed by `max_group_size` and maximum space complexity specified by `sc_target`, Then finds the contraction order inside each group with the greedy search algorithm. Other arguments are

  * `size_dict`, a dictionary that specifies leg dimensions,
  * `sc_target` is the target space complexity, defined as `log2(number of elements in the largest tensor)`,
  * `max_group_size` is the maximum size that allowed to used greedy search,
  * `βs` is a list of inverse temperature `1/T`,
  * `niters` is the number of iteration in each temperature,
  * `ntrials` is the number of repetition (with different random seeds),
  * `sub_optimizer`, the optimizer for the bipartited sub graphs, one can choose `GreedyMethod()` or `TreeSA()`,
  * `initializer`, the partition configuration initializer, one can choose `:random` or `:greedy` (slow but better).

### References

  * [Hyper-optimized tensor network contraction](https://arxiv.org/abs/2002.01935)
