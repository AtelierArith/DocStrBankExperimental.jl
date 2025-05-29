```
p8est_balance_ext(p8est_, btype, init_fn, replace_fn)
```

2:1 balance the size differences of neighboring elements in a forest.

### Parameters

  * `p8est`:[in,out] The `p8est` to be worked on.
  * `btype`:[in] Balance type (face, edge, or corner/full). Corner balance is almost never required when discretizing a PDE; just causes smoother mesh grading.
  * `init_fn`:[in] Callback function to initialize the user_data which is already allocated automatically.
  * `replace_fn`:[in] Callback function that allows the user to change incoming quadrants based on the quadrants they replace.

### Prototype

```c
void p8est_balance_ext (p8est_t * p8est, p8est_connect_type_t btype, p8est_init_t init_fn, p8est_replace_t replace_fn);
```
