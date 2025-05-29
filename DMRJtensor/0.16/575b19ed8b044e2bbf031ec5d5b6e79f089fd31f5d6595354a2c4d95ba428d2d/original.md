```
Lbound = makeBoundary(dualpsi,psi,mpovec...[,left=true,rightind=3])
```

Creates boundary tensor `Lbound` from an input MPS `psi`, dual MPS `dualpsi`, and any number of MPOs `mpovec`; `left` controls whether to make the left or right boundary tensor; `rightind` is the number index of the MPS that corresponds to the right link index

#Note:

  * dense tensors are just ones(1,1,1,...)

Current environment convention is      LEFT              RIGHT    +–<– 1          3 –-<–+    |                         |    |                         |    +–>– 2          2 –->–+    |                         |    |                         |    +–>– 3          1 –->–+

See also: [`makeEnds`](@ref)
