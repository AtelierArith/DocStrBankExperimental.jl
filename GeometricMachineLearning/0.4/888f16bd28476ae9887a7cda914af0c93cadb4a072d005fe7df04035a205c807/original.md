```
StiefelLieAlgHorMatrix(D::AbstractMatrix, n::Integer)
```

Take a big matrix as input and build an instance of `StiefelLieAlgHorMatrix`.

The integer $N$ in $St(n, N)$ is the number of rows of `D`.

# Extended help

If the constructor is called with a big $N\times{}N$ matrix, then the projection is performed the following way: 

$$
\begin{pmatrix}
A & B_1  \\
B_2 & D
\end{pmatrix} \mapsto 
\begin{pmatrix}
\mathrm{skew}(A) & -B_2^T \\ 
B_2 & \mathbb{O}
\end{pmatrix}.
$$

The operation $\mathrm{skew}:\mathbb{R}^{n\times{}n}\to\mathcal{S}_\mathrm{skew}(n)$ is the skew-symmetrization operation. This is equivalent to calling of [`SkewSymMatrix`](@ref) with an $n\times{}n$ matrix.

This can also be seen as the operation:

$$
D \mapsto \Omega(E, DE) = \mathrm{skew}\left(2 \left(\mathbb{I} - \frac{1}{2} E E^T \right) DE E^T\right).
$$

Also see [`GeometricMachineLearning.Ω`](@ref).
