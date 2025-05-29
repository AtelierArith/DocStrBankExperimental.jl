```
PeriodicTorsion(; periodicities, phases, ks, proper)
```

A periodic torsion angle between four atoms.

`phases` are in radians. The potential energy is defined as

$$
V(\phi) = \sum_{n=1}^N k_n (1 + \cos(n \phi - \phi_{s,n}))
$$
