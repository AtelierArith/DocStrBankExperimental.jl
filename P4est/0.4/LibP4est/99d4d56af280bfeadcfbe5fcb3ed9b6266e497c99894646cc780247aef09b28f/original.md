```
p4est_connectivity_new_disk_nonperiodic()
```

Create a connectivity structure for a five-tree flat spherical disk. This disk can just as well be used as a square to test non-Cartesian maps. Without any mapping this connectivity covers the square [-3, 3]**2.

### Returns

Initialized and usable connectivity.

### Prototype

```c
p4est_connectivity_t *p4est_connectivity_new_disk_nonperiodic (void);
```
