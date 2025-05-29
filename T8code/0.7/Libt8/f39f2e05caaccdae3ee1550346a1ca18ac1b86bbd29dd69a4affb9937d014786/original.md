```
t8_forest_ghost_destroy(pghost)
```

Verify that a ghost structure has only one reference left and destroy it. This function is preferred over t8*ghost*unref when it is known that the last reference is to be deleted.

# Arguments

  * `pghost`:[in,out] This ghost structure must have a reference count of one. It can be in any state (committed or not). Then it effectively calls t8*forest*ghost_unref.

### Prototype

```c
void t8_forest_ghost_destroy (t8_forest_ghost_t *pghost);
```
