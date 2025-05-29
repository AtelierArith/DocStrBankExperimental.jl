```
orbit(g::SiteGroup)  -->  Vector{WyckoffPosition}
```

Compute the orbit of the Wyckoff position associated with the site symmetry group `g`.

## Extended help

The orbit of a Wyckoff position $\mathbf{r}$ in a space group $G$ is defined as the set of inequivalent points in the unit cell that can be obtained by applying the elements of $G$ to $\mathbf{r}$. Equivalently, every element of the orbit of $\mathbf{r}$ can be written as the composition of a coset representative of the Wyckoff position's site group in $G$ with $\mathbf{r}$.
