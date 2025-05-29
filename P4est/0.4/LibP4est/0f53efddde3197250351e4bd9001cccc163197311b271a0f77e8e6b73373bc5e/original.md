```
p8est_balance(p8est_, btype, init_fn)
```

2:1 balance the size differences of neighboring elements in a forest.

### Parameters

  * `p8est`:[in,out] The `p8est` to be worked on.
  * `btype`:[in] Balance type (face, edge, or corner/full). Examples: Finite volume or discontinuous Galerkin methods only require face balance. Continuous finite element methods usually require edge balance. Corner balance is almost never required mathematically; it just produces a smoother mesh grading.
  * `init_fn`:[in] Callback function to initialize the user_data which is already allocated automatically.

### Prototype

```c
void p8est_balance (p8est_t * p8est, p8est_connect_type_t btype, p8est_init_t init_fn);
```
