```
t8_forest_ref(forest)
```

Increase the reference counter of a forest.

# Arguments

  * `forest`:[in,out] On input, this forest must exist with positive reference count. It may be in any state.

### Prototype

```c
void t8_forest_ref (t8_forest_t forest);
```
