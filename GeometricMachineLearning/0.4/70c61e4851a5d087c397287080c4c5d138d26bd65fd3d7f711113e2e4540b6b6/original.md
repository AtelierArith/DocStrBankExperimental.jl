```
GrassmannLayer(n, N)
```

Make an instance of `GrassmannLayer`.

This layer performs simple multiplication with an element of the Grassmann manifold, i.e.

$$
    \mathtt{GrassmannLayer}: x \mapsto Ax,
$$

where $A$ is a representation of an element in the Grassmann manifold, i.e. $\mathcal{A} = \mathrm{span}(A)$.
