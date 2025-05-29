```
Lenv,Renv = makeEnds(psi[,mpovec,Lbound=,Rbound=])
```

Generates first and last environment tensors for a given system of variable MPOs.  Same as other implementation but `dualpsi`=`psi`

# Arguments:

  * `psi::MPS`: MPS
  * `mpovec::MPO`: MPOs
  * `Lbound::TensType`: left boundary
  * `Rbound::TensType`: right boundary

Current environment convention is      LEFT              RIGHT    +–<– 1          3 –-<–+    |                         |    |                         |    +–>– 2          2 –->–+    |                         |    |                         |    +–>– 3          1 –->–+
