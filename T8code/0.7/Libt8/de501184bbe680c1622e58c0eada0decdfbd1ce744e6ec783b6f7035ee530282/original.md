```
t8_forest_ghost_remote_first_tree(forest, remote)
```

Return the first local ghost tree of a remote rank.

# Arguments

  * `forest`:[in] A forest with constructed ghost layer.
  * `remote`:[in] A remote rank of the ghost layer in *forest*.

# Returns

The ghost tree id of the first ghost tree that stores ghost elements of *remote*.

### Prototype

```c
t8_locidx_t t8_forest_ghost_remote_first_tree (t8_forest_t forest, int remote);
```
