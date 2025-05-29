```
RAT(num_features; input_func::Function = RAT_InputFunc(Literal), num_nodes_region, num_nodes_leaf, rg_depth, rg_replicas, num_nodes_root = 1, balance_childs_parents = true)
```

Generate a RAT-SPN structure. First, it generates a random region graph with `depth`, and `replicas`.  Then uses the random region graph to generate a ProbCircuit conforming to that region graph.

  * `num_features`: Number of features in the dataset, assuming x*1...x*n
  * `input_func`: Function to generate a new input node for variable when calling `input_func(var)`.

The list of hyperparamters are:

  * `rg_depth`: how many layers to do splits in the region graph
  * `rg_replicas`: number of replicas or paritions (replicas only used for the root region; for other regions only 1 parition (inner nodes), or 0 parition for leaves)
  * `num_nodes_root`: number of sum nodes in the root region
  * `num_nodes_leaf`: number of sum nodes per leaf region
  * `num_nodes_region`: number of in each region except root and leaves
  * `num_splits`: number of splits for each parition; split variables into random equaly sized regions
