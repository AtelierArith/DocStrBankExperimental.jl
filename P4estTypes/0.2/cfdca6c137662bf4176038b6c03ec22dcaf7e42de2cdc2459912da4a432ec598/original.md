```
LNodes{X,P}
```

Stores a parallel numbering of Lobatto nodes for a `Pxest{X}`.

# Fields

  * `pointer`: The pointer (of type `P`) can be a pointer to either a `P4estTypes.P4est.p4est_lnodes_t` or a `P4estTypes.P4est.p8est_lnodes_t`.  See the help documentation for these types for more information about the underlying p4est structures.
  * `comm`: The MPI Communicator that includes the ranks participating in the lnods.

# See also

  * [`lnodes`](@ref): a function used to construct `LNodes`
