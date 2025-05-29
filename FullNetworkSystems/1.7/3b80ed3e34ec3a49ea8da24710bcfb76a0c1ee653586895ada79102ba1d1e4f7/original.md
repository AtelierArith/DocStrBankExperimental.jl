```
compute_ptdf(system::System; block_size, reference_bus_index) -> KeyedArray
compute_ptdf(buses::Buses, branches::Branches; block_size, reference_bus_index) -> KeyedArray
```

Takes a system, or data for that system, representing a `M` branch, `N` bus grid and returns the `M * N` DC-Power Transfer Distribution Factor (DC-PTDF) matrix of the network.

For a ~15,000 bus system with aggregated borders, this is expected to take ~1 minute.

# Keywords

  * `block_size=13_000`: Block size to be used when partitioning a big matrix for inversion.
  * `reference_bus=first(keys(buses))`: The name of the reference bus.

# Output

  * `::KeyedArray`: The PTDF matrix; the axes contain the branch and bus names.

!!! note
    The input data must have no isolated components or islands.

