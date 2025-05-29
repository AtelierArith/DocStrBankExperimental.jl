```
t8_forest_is_committed(forest)
```

Check whether a forest is not NULL, initialized and committed. In addition, it asserts that the forest is consistent as much as possible.

# Arguments

  * `forest`:[in] This forest is examined. May be NULL.

# Returns

True if forest is not NULL and t8*forest*init has been called on it as well as t8*forest*commit. False otherwise.

### Prototype

```c
int t8_forest_is_committed (t8_forest_t forest);
```
