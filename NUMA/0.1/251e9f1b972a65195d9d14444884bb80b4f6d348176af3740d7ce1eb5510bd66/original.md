```julia
numa_allocate_cpumask() -> NUMA.Bitmask

```

Returns a bitmask of a size equal to the kernel's cpu mask. In other words, large enough to represent all cpus.
