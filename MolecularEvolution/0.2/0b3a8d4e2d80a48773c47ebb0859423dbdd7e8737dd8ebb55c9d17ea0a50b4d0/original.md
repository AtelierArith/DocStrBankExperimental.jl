# Constructor

```
LazyPartition{PType}()
```

Initialize an empty `LazyPartition` that is meant for wrapping a partition of type `PType`.

# Description

With this data structure, you can wrap a partition of choice.  The idea is that in some message passing algorithms, there is only a wave of partitions which need to actualize.  For instance, a wave following a root-leaf path, or a depth-first traversal. In which case, we can be more economical with our memory consumption. With a worst case memory complexity of O(log(n)), where n is the number of nodes, functionality is provided for:

  * `log_likelihood!`
  * `felsenstein!`
  * `sample_down!`

!!! note
    For successive `felsenstein!` calls, we need to extract the information at the root somehow after each call. This can be done with e.g. `total_LL` or `site_LLs`.


# Further requirements

Suppose you want to wrap a partition of `PType` with `LazyPartition`:

  * If you're calling `log_likelihood!` and `felsenstein!`:

      * `obs2partition!(partition::PType, obs)` that transforms an observation to a partition.
  * If you're calling `sample_down!`:

      * `partition2obs(partition::PType)` that returns the most likely state from a partition, inverts `obs2partition!`.
