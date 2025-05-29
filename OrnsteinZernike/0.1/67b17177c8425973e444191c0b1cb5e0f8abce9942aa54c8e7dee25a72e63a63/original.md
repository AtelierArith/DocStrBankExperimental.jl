```
LennardJones
```

Implements the Lennard-Jones pair interaction $u(r) = 4\epsilon [(\sigma/r)^{12} - (\sigma/r)^6]$.

Expects values `ϵ` and `σ`, which respecively are the strength of the potential and particle size. 

Example:

```julia
potential = LennardJones(1.0, 2.0)
```
