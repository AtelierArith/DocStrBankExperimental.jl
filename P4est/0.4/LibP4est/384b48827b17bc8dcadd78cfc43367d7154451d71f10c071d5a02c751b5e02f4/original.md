```
p6est_refine_columns(p6est_, refine_recursive, refine_fn, init_fn)
```

Refine the columns of a sheet.

### Parameters

  * `p6est`:[in,out] The forest is changed in place.
  * `refine_recursive`:[in] Boolean to decide on recursive refinement.
  * `refine_fn`:[in] Callback function that must return true if a column shall be refined into smaller columns. If refine_recursive is true, refine_fn is called for every existing and newly created column. Otherwise, it is called for every existing column. It is possible that a refinement request made by the callback is ignored. To catch this case, you can examine whether init_fn gets called, or use [`p6est_refine_columns_ext`](@ref) in p6est_extended.h and examine whether replace_fn gets called.
  * `init_fn`:[in] Callback function to initialize the user_data of newly created layers within columns, which are already allocated. This function pointer may be NULL.

### Prototype

```c
void p6est_refine_columns (p6est_t * p6est, int refine_recursive, p6est_refine_column_t refine_fn, p6est_init_t init_fn);
```
