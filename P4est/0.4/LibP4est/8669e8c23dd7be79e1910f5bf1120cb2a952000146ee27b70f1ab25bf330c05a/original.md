```
p8est_is_balanced(p8est_, btype)
```

Check a forest to see if it is balanced.

This function builds the ghost layer and discards it when done.

### Parameters

  * `p8est`:[in] The `p8est` to be tested.
  * `btype`:[in] Balance type (face, edge, corner or default, full).

### Returns

Returns true if balanced, false otherwise.

### Prototype

```c
int p8est_is_balanced (p8est_t * p8est, p8est_connect_type_t btype);
```
