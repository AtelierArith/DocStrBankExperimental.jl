```
t8_forest_set_ghost_ext(forest, do_ghost, ghost_type, ghost_version)
```

Like t8*forest*set*ghost but with the additional options to change the ghost algorithm. This is used for debugging and timing the algorithm. An application should almost always use t8*forest*set*ghost.

# Arguments

  * `ghost_version`:[in] If 1, the iterative ghost algorithm for balanced forests is used. If 2, the iterative algorithm for unbalanced forests. If 3, the top-down search algorithm for unbalanced forests.

# See also

[`t8_forest_set_ghost`](@ref)

### Prototype

```c
void t8_forest_set_ghost_ext (t8_forest_t forest, int do_ghost, t8_ghost_type_t ghost_type, int ghost_version);
```
