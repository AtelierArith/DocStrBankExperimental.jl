```
GrassmannLieAlgHorMatrix(D::AbstractMatrix, n::Integer)
```

Take a big matrix as input and build an instance of `GrassmannLieAlgHorMatrix`.

The integer $N$ in $Gr(n, N)$ here is the number of rows of `D`.

# Extended help

If the constructor is called with a big $N\times{}N$ matrix, then the projection is performed the following way: 

$$
\begin{pmatrix}
A & B_1  \\
B_2 & D
\end{pmatrix} \mapsto 
\begin{pmatrix}
\bar{\mathbb{O}} & -B_2^T \\ 
B_2 & \mathbb{O}
\end{pmatrix}.
$$

This can also be seen as the operation:

$$
D \mapsto \Omega(E, DE - EE^TDE),
$$

where $\Omega$ is the horizontal lift [`GeometricMachineLearning.Ω`](@ref).
