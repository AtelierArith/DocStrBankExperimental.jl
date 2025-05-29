```
MixedCell
```

Data structure representing a (fine) mixed cell.

## Fields

  * `indices::Vector{NTuple{2, Int}}`: The columns of the support creating the mixed cell.
  * `normal::Vector{Float64}`: The inner normal vector of the lifted mixed cell.
  * `β::Vector{Float64}`: The vector $(\min_{a \in A_i} ⟨a,γ⟩)_i$ where $γ$ is `normal`.
  * `volume::Int`: The volume of the mixed cell.
