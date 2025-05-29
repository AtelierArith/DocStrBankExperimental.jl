```
applyandadd!(gate::CliffordGate, pstr, coeff, theta, output_psum; kwargs...)
```

Overload of `applyandadd!` for `CliffordGate` gates. Use `set!()` instead of `add!()` because Clifford gates create non-overlapping Pauli strings. `applytoall!` does not need to be adapted.
