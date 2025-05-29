```
t8_forest_new_adapt(forest_from, adapt_fn, recursive, do_face_ghost, user_data)
```

Build a adapted forest from another forest.

!!! note
    This is equivalent to calling t8*forest*init, t8*forest*set*adapt, t8*forest*set*ghost, and t8*forest*commit


# Arguments

  * `forest_from`:[in] The forest to refine
  * `adapt_fn`:[in] Adapt function to use
  * `replace_fn`:[in] Replace function to use
  * `recursive`:[in] If true adptation is recursive
  * `do_face_ghost`:[in] If true, a layer of ghost elements is created for the forest.
  * `user_data`:[in] If not NULL, the user data pointer of the forest is set to this value.

# Returns

A new forest that is adapted from *forest_from*.

### Prototype

```c
t8_forest_t t8_forest_new_adapt (t8_forest_t forest_from, t8_forest_adapt_t adapt_fn, int recursive, int do_face_ghost, void *user_data);
```
