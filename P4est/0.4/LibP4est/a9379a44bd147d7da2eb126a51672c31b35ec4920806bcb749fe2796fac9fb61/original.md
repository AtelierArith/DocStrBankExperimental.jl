```
p6est_refine_layers(p6est_, refine_recursive, refine_fn, init_fn)
```

Refine the layers within the columns of a sheet.

### Parameters

  * `p6est`:[in,out] The forest is changed in place.
  * `refine_recursive`:[in] Boolean to decide on recursive refinement.
  * `refine_fn`:[in] Callback function that must return true if a layer shall be refined into smaller layers. If refine_recursive is true, refine_fn is called for every existing and newly created layer. Otherwise, it is called for every existing layer. It is possible that a refinement request made by the callback is ignored. To catch this case, you can examine whether init_fn gets called, or use [`p6est_refine_layers_ext`](@ref) in p6est_extended.h and examine whether replace_fn gets called.
  * `init_fn`:[in] Callback function to initialize the user_data of newly created layers, which are already allocated. This function pointer may be NULL.

### Prototype

```c
void p6est_refine_layers (p6est_t * p6est, int refine_recursive, p6est_refine_layer_t refine_fn, p6est_init_t init_fn);
```
