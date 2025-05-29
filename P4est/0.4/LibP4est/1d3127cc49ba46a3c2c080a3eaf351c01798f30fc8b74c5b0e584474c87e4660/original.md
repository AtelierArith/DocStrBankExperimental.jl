```
p6est_balance_ext(p6est_, btype, max_diff, min_diff, init_fn, replace_fn)
```

2:1 balance the size differences of neighboring elements in a forest.

### Parameters

  * `p6est`:[in,out] The `p6est` to be worked on.
  * `btype`:[in] Balance type (face or corner/full). Corner balance is almost never required when discretizing a PDE; just causes smoother mesh grading.
  * `max_diff`:[in] The maximum difference between the horizontal refinement level and the vertical refinement level
  * `min_diff`:[in] The minimum difference between the horizontal refinement level and the vertical refinement level
  * `init_fn`:[in] Callback function to initialize the user_data which is already allocated automatically.
  * `replace_fn`:[in] Callback function that allows the user to change incoming quadrants based on the quadrants they replace.

### Prototype

```c
void p6est_balance_ext (p6est_t * p6est, p8est_connect_type_t btype, int max_diff, int min_diff, p6est_init_t init_fn, p6est_replace_t replace_fn);
```
