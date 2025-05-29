```
applytoall!(gate, theta psum, output_psum; kwargs...)
```

2nd-level function below `applymergetruncate!` that applies one gate to all Pauli strings in `psum`, moving results into `output_psum` by default. After this functions, Pauli strings in remaining in `psum` and `output_psum` are merged. This function can be overwritten for a custom gate if the lower-level functions `applyandadd!` and `apply` are not sufficient. In particular, this function can be used to manipulate both `psum` and `output_psum` at the same time to reduce memory movement. Note that manipulating `psum` on anything other than the current Pauli string will likely lead to errors. See the `4-custom-gates.ipynb` for examples of how to define custom gates.
