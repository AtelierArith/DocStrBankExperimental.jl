```
sc_list_init(list, allocator)
```

Initialize a list object with an external link allocator.

### Parameters

  * `list`:[in,out] List structure to be initialized.
  * `allocator`:[in] External memory allocator for [`sc_link_t`](@ref), which must exist already.

### Prototype

```c
void sc_list_init (sc_list_t * list, sc_mempool_t * allocator);
```
