```
PowerLaw
```

Implements the power law pair interaction $u(r) = \epsilon (\sigma/r)^{n}$.

Expects values `ϵ`, `σ`, and `n`, which respecively are the strength of the potential and particle size. 

Example:

```julia
potential = PowerLaw(1.0, 2.0, 8)
```
