```
function set_bin_dirs(;qe=missing, mpi=missing, pseudodir=missing, templatedir=missing, wannier=missing)
```

Set directories where things like quantum espresso bins are located. If run with everything missing, instead print current dirs.

  * `qe` - set bin directory of quantum espresso. Needs pw and pp installed. No useful default.
  * `mpi` - set mpi command. something like "mpirun -np "
  * `pseudo` - set directory for pseudopotentials. Default is to use ../pseudo/gbrv_pbesol/ as distributed with this code
  * `template` - set directory for quantum espresso template files. Uses ../template_inputs/ by default.
