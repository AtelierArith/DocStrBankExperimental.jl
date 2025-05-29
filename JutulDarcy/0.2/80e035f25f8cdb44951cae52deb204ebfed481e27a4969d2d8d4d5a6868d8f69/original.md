```
ReservoirVoidageTarget(q, weights)
```

RESV target for history matching cases. The `weights` input should have one entry per phase (or pseudocomponent) in the system. The well control equation is then:

$|q_{ctrl} - \sum_i w_i q_i^s|$

where $q_i^s$ is the surface rate of phase $i$ and $w_i$ the weight of component stream $i$.

This constraint is typically set up from .DATA files for black-oil and immiscible cases.
