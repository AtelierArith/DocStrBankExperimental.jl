```
S0Graph(sig::AlgebraShape, S::Subspace{ComplexF64, 2})

S0Graph(g::AbstractGraph)
```

Represents an S₀-graph as defined in arxiv:1002.2514.

  * `n::Integer`: Dimension of Hilbert space A such that S ⊆ L(A)
  * `sig::Matrix{<:Integer}`: Structure of C*-algebra S₀
  * `S::Subspaces.Subspace{ComplexF64, 2}`: Subspace that defines the graph
  * `S0::Subspaces.Subspace{ComplexF64, 2}`: C*-algebra S₀
  * `S1::Subspaces.Subspace{ComplexF64, 2}`: Commutant of C*-algebra S₀
  * `D::Matrix{Float64}`: Block scaling array D from definition 23 of arxiv:2101.00162
