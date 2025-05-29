```
t8_forest_is_initialized(forest)
```

Check whether a forest is not NULL, initialized and not committed. In addition, it asserts that the forest is consistent as much as possible.

# Arguments

  * `forest`:[in] This forest is examined. May be NULL.

# Returns

True if forest is not NULL, t8*forest*init has been called on it, but not t8*forest*commit. False otherwise.

### Prototype

```c
int t8_forest_is_initialized (t8_forest_t forest);
```
