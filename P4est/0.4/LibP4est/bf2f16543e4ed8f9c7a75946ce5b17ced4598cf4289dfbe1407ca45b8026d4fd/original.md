```
p4est_connectivity_new_disk(periodic_a, periodic_b)
```

Create a connectivity structure for a five-tree flat spherical disk. This disk can just as well be used as a square to test non-Cartesian maps. Without any mapping this connectivity covers the square [-3, 3]**2.

!!! note
    The API of this function has changed to accept two arguments. You can query the #define `P4EST_CONN_DISK_PERIODIC` to check whether the new version with the argument is in effect.


The ordering of the trees is as follows: 4 1 2 3 0.

The outside x faces may be identified topologically. The outside y faces may be identified topologically. Both identifications may be specified simultaneously. The general shape and periodicity are the same as those obtained with p4est*connectivity*new*brick (1, 1, periodic\*a, periodic_b).

When setting *periodic_a* and *periodic_b* to false, the result is the same as that of p4est*connectivity*new*disk*nonperiodic.

### Parameters

  * `periodic_a`:[in] Bool to make disk periodic in x direction.
  * `periodic_b`:[in] Bool to make disk periodic in y direction.

### Returns

Initialized and usable connectivity.

### Prototype

```c
p4est_connectivity_t *p4est_connectivity_new_disk (int periodic_a, int periodic_b);
```
