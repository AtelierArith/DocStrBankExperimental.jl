```
t8_forest_set_ghost(forest, do_ghost, ghost_type)
```

Enable or disable the creation of a layer of ghost elements. On default no ghosts are created.

# Arguments

  * `forest`:[in] The forest.
  * `do_ghost`:[in] If non-zero a ghost layer will be created.
  * `ghost_type`:[in] Controls which neighbors count as ghost elements, currently only T8_GHOST_FACES is supported. This value is ignored if *do_ghost* = 0.

### Prototype

```c
void t8_forest_set_ghost (t8_forest_t forest, int do_ghost, t8_ghost_type_t ghost_type);
```
