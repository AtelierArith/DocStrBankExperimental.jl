```
p8est_connectivity_is_equivalent(conn1, conn2)
```

[`p8est_connectivity_is_equivalent`](@ref) This function compares two connectivities for equivalence: it returns *true* if they are the same connectivity, or if they have the same topology. The definition of topological sameness is strict: there is no attempt made to determine whether permutation and/or rotation of the trees makes the connectivities equivalent.

### Parameters

  * `conn1`:[in] a valid connectivity
  * `conn2`:[out] a valid connectivity

### Prototype

```c
int p8est_connectivity_is_equivalent (p8est_connectivity_t * conn1, p8est_connectivity_t * conn2);
```
