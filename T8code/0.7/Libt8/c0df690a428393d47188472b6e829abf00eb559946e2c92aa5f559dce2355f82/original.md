```
t8_forest_set_level(forest, level)
```

Set the initial refinement level to be used when **forest** is committed.

!!! note
    This setting cannot be combined with any of the derived forest methods (t8*forest*set*copy, t8*forest*set*adapt, t8*forest*set*partition, and t8*forest*set*balance) and overwrites any of these settings. If this function is used, then the forest is created from scratch as a uniform refinement of the specified cmesh (t8*forest*set*cmesh, t8*forest*set*scheme).


# Arguments

  * `forest`:[in,out] The forest whose level will be set.
  * `level`:[in] The initial refinement level of **forest**, when it is committed.

### Prototype

```c
void t8_forest_set_level (t8_forest_t forest, int level);
```
