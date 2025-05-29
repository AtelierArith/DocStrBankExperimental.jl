```
Oof2RNG(normrng, fmin, fknee, fsample)
```

Create a `Oof2RNG` RNG object. It requires a gaussian RNG generator in `normrng` (use `GaussRNG`), the minimum frequency (longest period) in `fmin`, the knee frequency and the sampling frequency. The measure unit of the three frequencies must be the same (e.g., Hz).

Use `randoof2` to draw samples from a `Oof2RNG` object, as in the following example:

```
rng = Oof2RNG(GaussRNG(), 1e-3, 1.0, 1e2)
print([randoof2(rng) for i in 1:4])
```
