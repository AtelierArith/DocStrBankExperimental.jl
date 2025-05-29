```
Lenv,Renv = makeEnds(dualpsi,psi[,mpovec,Lbound=,Rbound=])
```

Generates first and last environments for a given system of variable MPOs

# Arguments:

  * `dualpsi::MPS`: dual MPS
  * `psi::MPS`: MPS
  * `mpovec::MPO`: MPOs
  * `Lbound::TensType`: left boundary
  * `Rbound::TensType`: right boundary

Current environment convention is      LEFT              RIGHT    +–<– 1          3 –-<–+    |                         |    |                         |    +–>– 2          2 –->–+    |                         |    |                         |    +–>– 3          1 –->–+
