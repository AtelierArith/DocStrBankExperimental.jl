```
t8_forest_is_equal(forest_a, forest_b)
```

Check whether two committed forests have the same local elements.

!!! note
    This function is not collective. It only returns the state on the current rank.


# Arguments

  * `forest_a`:[in] The first forest.
  * `forest_b`:[in] The second forest.

# Returns

True if *forest_a* and *forest_b* do have the same number of local trees and each local tree has the same elements, that is t8*element*equal returns true for each pair of elements of *forest_a* and *forest_b*.

### Prototype

```c
int t8_forest_is_equal (t8_forest_t forest_a, t8_forest_t forest_b);
```
