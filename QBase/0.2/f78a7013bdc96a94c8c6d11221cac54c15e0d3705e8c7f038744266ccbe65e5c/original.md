```
planar_symmetric_qubit_kets( n :: Int64 ) :: Vector{Ket{Float64}}
```

Constructs a set of `n``Ket`s oriented symmetrically in the x-z-plane. Each ket is separated by a bloch angle of `2π/n`. The `Ket`s are constructed with the form:

$$
|\psi_j \rangle = \cos(j \pi/n) | 0\rangle + \sin(j \pi/n)|1\rangle
$$

where $j \in \{0,\cdots, (n-1)\}$.

A `DomainError` is thrown if `n < 2`.
