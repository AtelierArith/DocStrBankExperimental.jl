```
MarkedPoissonProcess{M,R,D}
```

Homogeneous temporal Poisson process with arbitrary mark distribution.

# Fields

  * `λ::R`: event rate.
  * `mark_dist::D`: mark distribution with sample type `M`.

# Constructor

```
MarkedPoissonProcess{M}(λ, mark_dist)
```
