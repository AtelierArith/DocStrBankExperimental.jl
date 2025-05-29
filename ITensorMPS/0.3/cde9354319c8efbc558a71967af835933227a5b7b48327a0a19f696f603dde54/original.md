```
DMRGObserver(ops::Vector{String},
             sites::Vector{<:Index};
             energy_tol=0.0,
             minsweeps=2,
             energy_type=Float64)
```

Construct a DMRGObserver, provide an array of `ops` of operator names which are strings recognized by the `op` function. Each of these operators will be measured on every site during every step of DMRG and the results recorded inside the DMRGOberver for later analysis. The array `sites` is the basis of sites used to define the MPS and MPO for the DMRG calculation.

Optionally, one can provide an energy tolerance used for early stopping, and minimum number of sweeps that must be done.

Optional keyword arguments:

  * energy_tol: if the energy from one sweep to the next no longer changes by more than this amount, stop after the current sweep
  * minsweeps: do at least this many sweeps
  * energy_type: type to use when storing energies at each step
