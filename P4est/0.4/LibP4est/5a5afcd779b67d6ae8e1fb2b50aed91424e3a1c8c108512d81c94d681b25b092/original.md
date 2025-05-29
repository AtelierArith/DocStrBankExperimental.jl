```
p8est_refine_ext(p8est_, refine_recursive, maxlevel, refine_fn, init_fn, replace_fn)
```

Refine a forest with a bounded refinement level and a replace option.

### Parameters

  * `p8est`:[in,out] The forest is changed in place.
  * `refine_recursive`:[in] Boolean to decide on recursive refinement.
  * `maxlevel`:[in] Maximum allowed refinement level (inclusive). If this is negative the level is restricted only by the compile-time constant QMAXLEVEL in `p8est.h`.
  * `refine_fn`:[in] Callback function that must return true if a quadrant shall be refined. If refine_recursive is true, refine_fn is called for every existing and newly created quadrant. Otherwise, it is called for every existing quadrant. It is possible that a refinement request made by the callback is ignored. To catch this case, you can examine whether init_fn or replace_fn gets called.
  * `init_fn`:[in] Callback function to initialize the user_data for newly created quadrants, which is guaranteed to be allocated. This function pointer may be NULL.
  * `replace_fn`:[in] Callback function that allows the user to change incoming quadrants based on the quadrants they replace; may be NULL.

### Prototype

```c
void p8est_refine_ext (p8est_t * p8est, int refine_recursive, int maxlevel, p8est_refine_t refine_fn, p8est_init_t init_fn, p8est_replace_t replace_fn);
```
