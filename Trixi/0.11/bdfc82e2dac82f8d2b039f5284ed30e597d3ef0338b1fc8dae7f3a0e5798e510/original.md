```
linear_structure(semi::AbstractSemidiscretization;
                 t0=zero(real(semi)))
```

Wraps the right-hand side operator of the semidiscretization `semi` at time `t0` as an affine-linear operator given by a linear operator `A` and a vector `b`.
