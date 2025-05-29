```
add_pairs!(eom::DifferentialEquation; ω_lc::Num, n=1)
```

Add a limit cycle harmonic `ω_lc` to the system Equivalent to adding `n` pairs of harmonics ω +- ω_lc for each existing ω.
