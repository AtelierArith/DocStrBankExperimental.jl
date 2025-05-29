```
geodesic(B̄::StiefelLieAlgHorMatrix)
```

Compute the geodesic of an element in [`StiefelLieAlgHorMatrix`](@ref).

# Implementation

Internally this is using:

$$
\mathbb{I} + B'\mathfrak{A}(B', B'')B'',
$$

with 

$$
\bar{B} = \begin{bmatrix}
    A & -B^T \\ 
    B & \mathbb{O}
\end{bmatrix} = \begin{bmatrix}  \frac{1}{2}A & \mathbb{I} \\ B & \mathbb{O} \end{bmatrix} \begin{bmatrix}  \mathbb{I} & \mathbb{O} \\ \frac{1}{2}A & -B^T  \end{bmatrix} =: B'(B'')^T.
$$

This is using a computationally efficient version of the matrix exponential $\mathfrak{A}$. 

See [`GeometricMachineLearning.𝔄`](@ref).
