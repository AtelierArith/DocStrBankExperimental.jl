```
LinearLayerP(n)
```

Make a linear layer of dimension $n\times{}n$ that only changes the $p$ component.

This is equivalent to a left multiplication by the matrix:

$$
\begin{pmatrix}
\mathbb{I} & \mathbb{O} \\ 
A & \mathbb{I}
\end{pmatrix}, 
$$

where $A$ is a [`SymmetricMatrix`](@ref).
