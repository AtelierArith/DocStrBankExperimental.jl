```
OofRNG(normrng, slope, fmin, fknee, fsample)
```

Create a `OofRNG` RNG object. It requires a gaussian RNG generator in `normrng` (use `GaussRNG`), the slope α of the noise in `slope`, the minimum frequency (longest period) in `fmin`, the knee frequency and the sampling frequency. The measure unit of the three frequencies must be the same (e.g., Hz).

Use `randoof` to draw samples from a `OofRNG` object, as in the following example:

```
rng = OofRNG(GaussRNG(), -1.5, 1e-3, 1.0, 1e2)
print([randoof(rng) for i in 1:4])
```
