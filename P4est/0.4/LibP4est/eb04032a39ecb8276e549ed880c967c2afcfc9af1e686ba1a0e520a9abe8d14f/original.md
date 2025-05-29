```
p6est_balance(p6est_, btype, init_fn)
```

Balance a forest.

### Parameters

  * `p6est`:[in] The `p6est` to be worked on.
  * `btype`:[in] Balance type (face, corner or default, full).
  * `init_fn`:[in] Callback function to initialize the user_data which is already allocated automatically.

### Prototype

```c
void p6est_balance (p6est_t * p6est, p8est_connect_type_t btype, p6est_init_t init_fn);
```
