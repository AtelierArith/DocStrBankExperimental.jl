```
PowerSpectrum(M, ρ, Q_op, ωlist, reverse; solver, verbose, filename, SOLVEROptions...)
```

Calculate power spectrum for the system in frequency domain where `P_op` will be automatically set as the adjoint of `Q_op`.

This function is equivalent to: `PowerSpectrum(M, ρ, Q_op', Q_op, ωlist, reverse; solver, verbose, filename, SOLVEROptions...)`
