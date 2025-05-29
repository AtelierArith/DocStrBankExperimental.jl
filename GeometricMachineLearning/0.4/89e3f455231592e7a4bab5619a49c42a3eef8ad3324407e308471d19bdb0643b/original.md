```
LinearLayerQ(n)
```

Make a linear layer of dimension $n\times{}n$ that only changes the $q$ component.

This is equivalent to a left multiplication by the matrix:

$$
\begin{pmatrix}
\mathbb{I} & A \\ 
\mathbb{O} & \mathbb{I}
\end{pmatrix}, 
$$

where $A$ is a [`SymmetricMatrix`](@ref).
