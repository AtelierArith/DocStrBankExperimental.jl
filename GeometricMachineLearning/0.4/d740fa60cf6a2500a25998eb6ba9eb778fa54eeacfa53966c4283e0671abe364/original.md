```
StiefelLieAlgHorMatrix(A::SkewSymMatrix, B::AbstractMatrix, N::Integer, n::Integer)
```

Build an instance of `StiefelLieAlgHorMatrix` based on a skew-symmetric matrix `A` and an arbitrary matrix `B`.

An element of StiefelLieAlgMatrix takes the form: 

$$
\begin{pmatrix}
A & B^T \\ B & \mathbb{O}
\end{pmatrix},
$$

where $A$ is skew-symmetric (this is [`SkewSymMatrix`](@ref) in `GeometricMachineLearning`).

Also see [`GrassmannLieAlgHorMatrix`](@ref).

# Extended help

`StiefelLieAlgHorMatrix` is the *horizontal component of the Lie algebra of skew-symmetric matrices* (with respect to the canonical metric).

The projection here is: $\pi:S \to SE$ where 

$$
E = \begin{bmatrix} \mathbb{I}_{n} \\ \mathbb{O}_{(N-n)\times{}n}  \end{bmatrix}.
$$

The matrix $E$ is implemented under [`StiefelProjection`](@ref) in `GeometricMachineLearning`.
