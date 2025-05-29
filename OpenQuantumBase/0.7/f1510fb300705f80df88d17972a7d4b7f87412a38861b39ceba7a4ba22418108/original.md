```julia
correlation(t1, t2, bath)

```

Calculate the two point correlation function $C(t1, t2)$ of `bath`. Fall back to `correlation(t1-t2, bath)` unless otherwise defined.
