```
generalized_bell_kets( dim :: Int64 ) :: Vector{Ket{Float64}}
```

The Bell basis for entangled bipartite quantum states each of dimension `dim`. Each state is constructed by

$$
|\Psi^p_c\rangle = \frac{1}{\sqrt{d}}\sum_{j=0}^{d-1} e^{i2\pi pj/d}|j\rangle |\mod(j+c,d)\rangle
$$

where $p,c\in \{0,\cdots, (d-1)\}$ and $d$ is `dim`. When iterated, $c$ is the major index and $p$ is the minor index.

A `DomainError` is thrown if `dim ≥ 2` is not satisfied.
