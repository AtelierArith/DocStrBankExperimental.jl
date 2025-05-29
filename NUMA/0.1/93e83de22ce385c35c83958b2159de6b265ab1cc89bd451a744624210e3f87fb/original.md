```julia
numa_set_membind(bm::NUMA.Bitmask)

```

Sets the memory allocation mask. The task will only allocate memory from the nodes set in the given nodemask. Passing an empty nodemask or a nodemask that contains nodes other than those in the mask returned by `numa_get_mems_allowed()` will result in an error.
