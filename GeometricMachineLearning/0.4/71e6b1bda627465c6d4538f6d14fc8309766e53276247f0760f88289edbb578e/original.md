```
cayley(B̄::StiefelLieAlgHorMatrix)
```

Compute the Cayley retraction of `B`.

# Implementation

Internally this is using 

$$
\mathrm{Cayley}(\bar{B}) = \mathbb{I} + \frac{1}{2} B' (\mathbb{I}_{2n} - \frac{1}{2} (B'')^T B')^{-1} (B'')^T (\mathbb{I} + \frac{1}{2} B),
$$

with

$$
\bar{B} = \begin{bmatrix}
    A & -B^T \\ 
    B & \mathbb{O}
\end{bmatrix} = \begin{bmatrix}  \frac{1}{2}A & \mathbb{I} \\ B & \mathbb{O} \end{bmatrix} \begin{bmatrix}  \mathbb{I} & \mathbb{O} \\ \frac{1}{2}A & -B^T  \end{bmatrix} =: B'(B'')^T,
$$

i.e. $\bar{B}$ is expressed as a product of two $N\times{}2n$ matrices.
