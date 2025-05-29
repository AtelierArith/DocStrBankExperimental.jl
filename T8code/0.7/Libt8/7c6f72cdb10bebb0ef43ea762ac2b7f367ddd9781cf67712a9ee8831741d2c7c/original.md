```
t8_forest_no_overlap(forest)
```

Check whether the forest has local overlapping elements.

!!! note
    This function is collective, but only checks local overlapping on each process.


# Arguments

  * `forest`:[in] The forest to consider.

# Returns

True if *forest* has no elements which are inside each other.

# See also

[`t8_forest_partition_test_boundary_element`](@ref) if you also want to test for  global overlap across the process boundaries.

### Prototype

```c
int t8_forest_no_overlap (t8_forest_t forest);
```
