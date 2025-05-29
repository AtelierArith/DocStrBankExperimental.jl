```
LineConnectivity <:AbstractConnectivity
```

A data structure which describes the linear qubit connectivity of an Anyon System's QPU. This connectivity type is encountered in `QPUs` such as the [`AnyonYukonQPU`](@ref).

# Fields

  * `dimension         ::Int` – Number of qubits for this connectivity.
  * `excluded_positions::Vector{Int}` – Optional: List of qubits on the connectivity which                                      are disabled and cannot perform operations. Elements                                      in `Vector` must be unique.
  * `excluded_connections::Vector{Tuple{Int, Int}}` – Optional: List of connections between                                                    qubits which are disabled and cannot                                                    perform 2-qubit gates. Elements in                                                    `Vector` must be unique. Each                                                    connection is provided as a `Tuple` of                                                    qubit indices.

!!! note
    Every excluded connection is sorted in ascending order (i.e. connection (2, 1) will be changed to (1, 2)).


# Example

```jldoctest
julia> connectivity = LineConnectivity(6)
LineConnectivity{6}
1──2──3──4──5──6

julia> connectivity = LineConnectivity(6, [1,2,3], [(3, 2), (3, 4)])
LineConnectivity{6}
1──2──3──4──5──6
excluded positions: [1, 2, 3]
excluded connections: [(2, 3), (3, 4)]

```
