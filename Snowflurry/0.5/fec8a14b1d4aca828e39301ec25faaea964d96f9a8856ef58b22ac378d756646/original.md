```
LatticeConnectivity <:AbstractConnectivity
```

A data structure which describes the two-dimensional lattice qubit connectivity of an Anyon System's QPU. This connectivity type is encountered in `QPUs` such as the [`AnyonYamaskaQPU`](@ref).

# Fields

  * `qubits_per_printout_line::Vector{Int}` – Number of qubits in each line when constructing                                            the printout.
  * `dimensions              ::Vector{Int}` – Number of rows and columns (turned 45° in the                                            printout).
  * `excluded_positions      ::Vector{Int}` – Optional: List of qubits on the connectivity                                            which are disabled and cannot perform                                            operations. Elements in `Vector` must be                                            unique.
  * `excluded_connections::Vector{Tuple{Int, Int}}` – Optional: List of connections between                                                    qubits which are disabled and cannot                                                    perform 2-qubit gates. Elements in                                                    `Vector` must be unique. Each                                                    connection is provided as a `Tuple` of                                                    qubit indices.

# Example

The following lattice has 3 rows, where each row has 4 elements. The rows contain qubits  `[1, 2, 3, 4]`, `[ 5, 6, 7, 8]`, and `[9, 10, 11, 12]`.

The corresponding `qubits_per_printout_line` field is `[1, 3, 3, 3, 2]`. It contains the number of qubits in each line of the printed representation.

```jldoctest
julia> connectivity = LatticeConnectivity(3, 4)
LatticeConnectivity{3,4}
        1 
        | 
  9 ──  5 ──  2 
        |     | 
       10 ──  6 ──  3 
              |     | 
             11 ──  7 ──  4 
                    |     | 
                   12 ──  8 


```

Lattices of arbitrary dimensions can be built:

```jldoctest
julia> connectivity = LatticeConnectivity(6, 4)
LatticeConnectivity{6,4}
              1 
              | 
        9 ──  5 ──  2 
        |     |     | 
 17 ── 13 ── 10 ──  6 ──  3 
  |     |     |     |     | 
 21 ── 18 ── 14 ── 11 ──  7 ──  4 
        |     |     |     |     | 
       22 ── 19 ── 15 ── 12 ──  8 
              |     |     | 
             23 ── 20 ── 16 
                    | 
                   24 
```

Optionally, lattices with excluded positions can be defined:

```jldoctest
julia> connectivity = LatticeConnectivity(3, 4, [1, 5, 9])
LatticeConnectivity{3,4}
        1 
        | 
  9 ──  5 ──  2 
        |     | 
       10 ──  6 ──  3 
              |     | 
             11 ──  7 ──  4 
                    |     | 
                   12 ──  8 

excluded positions: [1, 5, 9]
```
