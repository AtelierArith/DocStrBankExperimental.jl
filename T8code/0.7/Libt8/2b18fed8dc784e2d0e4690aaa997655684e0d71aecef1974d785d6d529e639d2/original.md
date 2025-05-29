```
t8_forest_partition_test_boundary_element(forest)
```

Test if the last descendant of the last element of current rank has a smaller linear id than the stored first descendant of rank+1. If this is not the case, elements overlap.

!!! note
    *forest* must be committed before calling this function.


# Arguments

  * `forest`:[in] The forest.

### Prototype

```c
void t8_forest_partition_test_boundary_element (const t8_forest_t forest);
```
