```
KaHyParBipartite{RT,IT,GM}
KaHyParBipartite(; sc_target, imbalances=collect(0.0:0.005:0.8),
    max_group_size=40, greedy_config=GreedyMethod())
```

Optimize the einsum code contraction order using the KaHyPar + Greedy approach. This program first recursively cuts the tensors into several groups using KaHyPar, with maximum group size specifed by `max_group_size` and maximum space complexity specified by `sc_target`, Then finds the contraction order inside each group with the greedy search algorithm. Other arguments are

  * `sc_target` is the target space complexity, defined as `log2(number of elements in the largest tensor)`,
  * `imbalances` is a KaHyPar parameter that controls the group sizes in hierarchical bipartition,
  * `max_group_size` is the maximum size that allowed to used greedy search,
  * `greedy_config` is a greedy optimizer.

### References

  * [Hyper-optimized tensor network contraction](https://arxiv.org/abs/2002.01935)
  * [Simulating the Sycamore quantum supremacy circuits](https://arxiv.org/abs/2103.03074)
