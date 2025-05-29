```julia
struct MechanismState{X, M, C, JointCollection}
```

A `MechanismState` stores state information for an entire `Mechanism`. It contains the joint configuration and velocity vectors $q$ and $v$, and a vector of additional states $s$. In addition, it stores cache variables that depend on $q$ and $v$ and are aimed at preventing double work.

Type parameters:

  * `X`: the scalar type of the $q$, $v$, and $s$ vectors.
  * `M`: the scalar type of the `Mechanism`
  * `C`: the scalar type of the cache variables (`== promote_type(X, M)`)
  * `JointCollection`: the type of the `treejoints` and `nontreejoints` members (a `TypeSortedCollection` subtype)
