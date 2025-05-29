```
metropolis_sample(
    update!::AbstractUpdate,
    initial_tree::FelNode,
    models,
    num_of_samples;
    partition_list = 1:length(initial_tree.message),
    burn_in = 1000,
    sample_interval = 10,
    collect_LLs = false,
    collect_models = false,
    midpoint_rooting = false,
    ladderize = false,
)
```

Samples tree topologies from a posterior distribution using a custom `update!` function.

# Arguments

  * `update!`: A callable that takes (tree::FelNode, models) and updates `tree` and `models`. One call to `update!` corresponds to one iteration of the Metropolis algorithm.
  * `initial_tree`: An initial tree topology with the leaves populated with data, for the likelihood calculation.
  * `models`: A list of branch models.
  * `num_of_samples`: The number of tree samples drawn from the posterior.
  * `partition_list`: (eg. 1:3 or [1,3,5]) lets you choose which partitions to run over (but you probably want to sample with all partitions, the default option).
  * `burn_in`: The number of samples discarded at the start of the Markov Chain.
  * `sample_interval`: The distance between samples in the underlying Markov Chain (to reduce sample correlation).
  * `collect_LLs`: Specifies if the function should return the log-likelihoods of the trees.
  * `collect_models`: Specifies if the function should return the models.
  * `midpoint_rooting`: Specifies whether the drawn samples should be midpoint rerooted (Important! Should only be used for time-reversible branch models starting in equilibrium).

!!! note
    The leaves of the initial tree should be populated with data and felsenstein! should be called on the initial tree before calling this function.


# Returns

  * `samples`: The trees drawn from the posterior. Returns shallow tree copies, which needs to be repopulated before running felsenstein! etc.
  * `sample_LLs`: The associated log-likelihoods of the tree (optional).
  * `sample_models`: The models drawn from the posterior (optional). The models can be collapsed into it's parameters with `collapse_models`.
