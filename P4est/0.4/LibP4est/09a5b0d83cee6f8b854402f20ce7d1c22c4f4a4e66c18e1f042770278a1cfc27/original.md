```
p4est_balance(p4est_, btype, init_fn)
```

2:1 balance the size differences of neighboring elements in a forest.

### Parameters

  * `p4est`:[in,out] The `p4est` to be worked on.
  * `btype`:[in] Balance type (face or corner/full). Corner balance is almost never required when discretizing a PDE; just causes smoother mesh grading.
  * `init_fn`:[in] Callback function to initialize the user_data which is already allocated automatically.

### Prototype

```c
void p4est_balance (p4est_t * p4est, p4est_connect_type_t btype, p4est_init_t init_fn);
```
