```
is_score_expected(noise_score::NoiseScore, z_score_cutoff::Real)
is_score_expected(noise_score::NoiseScore, z_score_cutoff_lower::Real, z_score_cutoff_upper::Real)
```

Returns a Boolean indicating whether the z-scores in `noise_score` are within the specified cutoffs, and projection improves the z-scores as expected.
