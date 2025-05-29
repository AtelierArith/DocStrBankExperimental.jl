```
t8_forest_iterate_replace(forest_new, forest_old, replace_fn)
```

Given two forest where the elements in one forest are either direct children or parents of the elements in the other forest compare the two forests and for each refined element or coarsened family in the old one, call a callback function providing the local indices of the old and new elements.

!!! note
    To pass a user pointer to *replace_fn* use t8*forest*set*user*data and t8*forest*get*user*data.


# Arguments

  * `forest_new`:[in] A forest, each element is a parent or child of an element in *forest_old*.
  * `forest_old`:[in] The initial forest.
  * `replace_fn`:[in] A replace callback function.

### Prototype

```c
void t8_forest_iterate_replace (t8_forest_t forest_new, t8_forest_t forest_old, t8_forest_replace_t replace_fn);
```
