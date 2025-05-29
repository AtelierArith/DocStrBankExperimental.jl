```julia
Probit <: CRRaoLink
```

A type representing the Probit link function, which is defined by the formula

$$
z\mapsto \mathbb{P}[Z\le z]
$$

where $Z\sim \text{Normal}(0, 1)$.
