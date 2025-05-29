```
t8_forest_ghost_create_balanced_only(forest)
```

Create one layer of ghost elements for a forest. This version only works with balanced forests and is the original algorithm from p4est: Scalable Algorithms For Parallel Adaptive Mesh Refinement On Forests of Octrees

!!! note
    The user should prefer t8*forest*ghost_create even for balanced forests.


# Arguments

  * `forest`:[in,out] The balanced forest/ *forest* must be committed before calling this function.

### Prototype

```c
void t8_forest_ghost_create_balanced_only (t8_forest_t forest);
```
