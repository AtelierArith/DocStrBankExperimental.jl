```
p4est_refine(p4est_, refine_recursive, refine_fn, init_fn)
```

Refine a forest.

### Parameters

  * `p4est`:[in,out] The forest is changed in place.
  * `refine_recursive`:[in] Boolean to decide on recursive refinement.
  * `refine_fn`:[in] Callback function that must return true if a quadrant shall be refined. If refine_recursive is true, refine_fn is called for every existing and newly created quadrant. Otherwise, it is called for every existing quadrant. It is possible that a refinement request made by the callback is ignored. To catch this case, you can examine whether init_fn gets called, or use [`p4est_refine_ext`](@ref) in p4est_extended.h and examine whether replace_fn gets called.
  * `init_fn`:[in] Callback function to initialize the user_data of newly created quadrants, which is already allocated. This function pointer may be NULL.

### Prototype

```c
void p4est_refine (p4est_t * p4est, int refine_recursive, p4est_refine_t refine_fn, p4est_init_t init_fn);
```
