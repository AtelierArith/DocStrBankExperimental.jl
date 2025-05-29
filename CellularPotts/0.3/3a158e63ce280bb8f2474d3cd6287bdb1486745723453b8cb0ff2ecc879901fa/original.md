```
ChemoTaxisPenalty(λ, Species)
```

A concrete type that encourages cells to move up or down a concentration gradient.

Two integer parameters control how cells protude:

  * `λ`: A parameter that controls the strength of this penalty
  * `Species`: The concentration profile for a species that should match the size of the cell space

Species concentration profile can be updated dynamically (e.g. by an ODE)

Supplying a positive λ will move cells up the gradient, negative values down the gradient.
