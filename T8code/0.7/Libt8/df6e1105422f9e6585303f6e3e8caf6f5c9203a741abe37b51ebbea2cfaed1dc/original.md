```
t8_forest_ghost_unref(pghost)
```

Decrease the reference count of a ghost structure. If the counter reaches zero, the ghost structure is destroyed. See also t8*forest*ghost_destroy, which is to be preferred when it is known that the last reference to a cmesh is deleted.

# Arguments

  * `pghost`:[in,out] On input, the ghost structure pointed to must exist with positive reference count. If the reference count reaches zero, the ghost structure is destroyed and this pointer is set to NULL. Otherwise, the pointer is not changed.

### Prototype

```c
void t8_forest_ghost_unref (t8_forest_ghost_t *pghost);
```
