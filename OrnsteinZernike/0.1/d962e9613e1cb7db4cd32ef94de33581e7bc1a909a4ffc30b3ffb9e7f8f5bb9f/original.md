```
BallonePastoreGalliGazzillo <: Closure
```

Implements the Ballone-Pastore-Galli-Gazzillo closure $b(r) = (1 + s \gamma(r))^{1/s} - \gamma(r) - 1 $. Here, $s$ is a free parameter that can be determined with thermodynamic consistency.

Example:

```julia
closure = BallonePastoreGalliGazzillo(1.5)
```

References:

Ballone, P., et al. "Additive and non-additive hard sphere mixtures: Monte Carlo simulation and integral equation results." Molecular Physics 59.2 (1986): 275-290.
