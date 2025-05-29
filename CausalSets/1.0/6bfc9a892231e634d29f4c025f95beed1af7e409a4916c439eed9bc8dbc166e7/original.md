```
continuous_relation_ratio(dim) -> Float64
```

Calculate the predicted continuum limit of the relation ratio $\langle \mathbf{R} \rangle / n^2$ for dimension `dim`, where $R$ is the number of relations as calculated by [`count_relations`](@ref), and $n$ is the number of atoms in the causet.

The predicted continuum limit is:

$$
\frac{\langle \mathbf{R} \rangle}{n^2} = \frac{Γ(d) Γ(d/2)}{4Γ(3d/2)}
$$

where `d` is the dimension.
