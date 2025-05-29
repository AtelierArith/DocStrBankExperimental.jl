```
p4est_is_balanced(p4est_, btype)
```

Check a forest to see if it is balanced.

This function builds the ghost layer and discards it when done.

### Parameters

  * `p4est`:[in] The `p4est` to be tested.
  * `btype`:[in] Balance type (face, corner or default, full).

### Returns

Returns true if balanced, false otherwise.

### Prototype

```c
int p4est_is_balanced (p4est_t * p4est, p4est_connect_type_t btype);
```
