```
flux_central(u_ll, u_rr, orientation_or_normal_direction, equations::AbstractEquations)
```

The classical central numerical flux `f((u_ll) + f(u_rr)) / 2`. When this flux is used as volume flux, the discretization is equivalent to the classical weak form DG method (except floating point errors).
