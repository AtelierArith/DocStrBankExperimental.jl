```julia
numa_bitmask_alloc() -> NUMA.Bitmask
numa_bitmask_alloc(n::Integer) -> NUMA.Bitmask

```

Allocates a bitmask structure and its associated bit mask. The memory allocated for the bit mask contains enough words (type `UInt64`) to contain `n` bits. If `n` isn't provided, `nnumanodes()` is used.

The bit mask is zero-filled.
