```
apply(filt::SavitzkyGolayFilter, spec::Spectrum, applyLLD=false)
```

Applys a function to the channel data in `spec` (with/wo the low-level discriminator.) The function can only be a function of the counts data and can not change the energy scale or spectrum properties.  The result is a Spectrum.

Example:

```
apply(SavitzkyGolayFilter{6,4}(),spec)
```
