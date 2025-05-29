```
lazyprep!(tree::FelNode, initial_message::Vector{<:Partition}; partition_list = 1:length(tree.message), direction::LazyDirection = LazyUp())
```

Extra, intermediate step of tree preparations between initializing messages across the tree and calling message passing algorithms with `LazyPartition`.

1. Perform a `lazysort!` on tree to obtain the optimal tree for a lazy `felsenstein!` prop, or a `sample_down!`.
2. Fix `tree.parent_message` to an initial message.
3. Preallocate sufficiently many inner partitions needed for a `felsenstein!` prop, or a `sample_down!`.
4. Specialized preparations based on the direction of the operations (`forward!`, `backward!`). `LazyDown` or `LazyUp`.

See also `LazyDown`, `LazyUp`.
