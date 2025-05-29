```
dmrg(hamiltonian, ::State; options...)
dmrg(hamiltonian, ::Simulation; options...)
```

optimize for ground state of the given Hamiltonian starting with state / simulation using dmrg.

Note that Dmrg does not work for mixed representations.

# Options

  * `nsweeps`: number of sweeps
  * `observer!`: observer (see `DmrgObserver`)
  * `limits`: constraints on the mps (`cutoff` and `maxdim may be vectors with different values for each sweep)
  * others identical to ITensorMPS.dmrg
