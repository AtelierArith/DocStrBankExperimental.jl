```
map_qubo(J::AbstractMatrix, h::AbstractVector) -> QUBOResult
```

Map a QUBO problem to a weighted MIS problem on a defected King's graph, where a QUBO problem is defined by the following Hamiltonian

$$
E(z) = -\sum_{i<j} J_{ij} z_i z_j + \sum_i h_i z_i
$$

!!! note
    The input coupling strength and onsite energies must be << 1.


A QUBO gadget is

```
⋅ ⋅ ● ⋅
● A B ⋅
⋅ C D ●
⋅ ● ⋅ ⋅
```

where `A`, `B`, `C` and `D` are weights of nodes that defined as

$$
\begin{align}
A = -J_{ij} + 4\\
B = J_{ij} + 4\\
C = J_{ij} + 4\\
D = -J_{ij} + 4
\end{align}
$$

The rest nodes: `●` have weights 2 (boundary nodes have weights $1 - h_i$).
