```
pX = rand(M::HamiltonianMatrices; σ::Real=1.0, vector_at=nothing)
rand!(M::HamiltonianMatrices, pX; σ::Real=1.0, vector_at=nothing)
```

Generate a random Hamiltonian matrix. Since these are a submanifold of $ℝ^{2n×2n}$, the same method applies for points and tangent vectors. This can also be done in-place of `pX`.

The construction is based on generating one normally-distributed $n×n$ matrix $A$ and two symmetric $n×n$ matrices $B, C$ which are then stacked:

$$
p = \begin{pmatrix} A & B\\ C & -A^{\mathrm{T}} \end{pmatrix}
$$
