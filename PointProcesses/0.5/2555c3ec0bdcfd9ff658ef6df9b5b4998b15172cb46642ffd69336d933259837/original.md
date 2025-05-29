```
logdensityof(pp, h)
```

Compute the log probability density function for a temporal point process `pp` applied to history `h`:

```
ℓ(h) = Σₖ log λ(tₖ|hₖ) - Λ(h)
```

The default method uses a loop over events combined with `integrated_ground_intensity`, but it should be reimplemented for specific processes if faster computation is possible.
