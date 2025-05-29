```
findWeylPoint(Hamiltonian::Function; N::Int=10, gapless::T=[1e-1, 1e-2, 1e-3, 1e-4], rounds::Bool=true) where {T<:AbstractVector{Float64}}
```

Arguments

  * Hamiltionian::Function: The Hamiltonian matrix with three-dimensional wavenumber `k` as an argument.
  * N::Int=10: The number of meshes when discretizing the Brillouin Zone. The $n$th iteration divides the Brillouin zone into $1/N^n$.
  * gapless<:AbstractVector{Float64}: The threshold that determines the state to be degenerate. The $n$th iteration adopts the threshold value of the $n$th value of the vector. The number of iterations can be varied by the length of the vector.
  * rounds::Bool=true: An option to round the value of the topological number to an integer value. The topological number returns a value of type `Int` when `true`, and a value of type `Float` when `false`.
