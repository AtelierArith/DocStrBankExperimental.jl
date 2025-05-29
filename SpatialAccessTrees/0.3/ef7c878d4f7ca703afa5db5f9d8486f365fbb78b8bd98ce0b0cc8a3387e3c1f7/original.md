```
index!(sat::Sat; <kwargs...>)
index!(sat::Sat, ipart::SatInitialPartition; <kwargs...>)
index!(sat::Sat, ipart::RandomInitialPartition; <kwargs...>)
```

Performs the indexing of the referenced dataset in the tree. It supports limited forms of multithreading, induced by initial partitioning schemes.

# Arguments

  * `sat`: The metric data structure.
  * `ipart`: initial partitioning scheme for the tree. It supports the following kinds of objects:

      * `SatInitialPartition()`: Traditional construction, default value. Each part is a SAT partition and will be processed by a thread on multithreading setups.
      * `RandomInitialPartition(nparts=Threads.nthreads(), shuffle=false)`:   construction that divides the dataset (randomly if `suffle=true`) in `nparts` disjoint parts. The resulting structure violates the SAT partitioning in a whole   and creates a kind of SAT forest that are fine SAT partitions. Useful to limit the height of the tree and for multiprocessing purporses, i.e., each part will be processed by a thread.

# Keyword arguments

  * `sortsat`: The strategy to create the spatial access tree, it heavily depends on the order of elements while it is build. It accepts:

      * `RandomSortSat()`: children are randomized (default value)
      * `ProximalSortSat()`: classical approach, near elements are put first.
      * `DistalSortSat()`: recent approach, distant elements are put first.
  * `minleaf`: Minimum number of children to perform a spatial access separation (half space partitioning)
