```
dispersion(swt::SpinWaveTheory, qpts)
```

Given a list of wavevectors `qpts` in reciprocal lattice units (RLU), returns excitation energies for each band. The return value `ret` is 2D array, and should be indexed as `ret[band_index, q_index]`.
