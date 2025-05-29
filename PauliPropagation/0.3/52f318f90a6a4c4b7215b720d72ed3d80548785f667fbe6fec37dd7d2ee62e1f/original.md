```
applyandadd!(gate, pstr, coefficient, theta, output_psum; kwargs...)
```

3rd-level function below `applymergetruncate!` that applies one gate to one Pauli string in `psum`, moving results into `output_psum` by default. This function can be overwritten for a custom gate if the lower-level function `apply` is not sufficient.  This is likely the the case if `apply` is not type-stable because it does not return a unique number of outputs.  E.g., a Pauli gate returns 1 or 2 (pstr, coefficient) outputs. See the `4-custom-gates.ipynb` for examples of how to define custom gates.
