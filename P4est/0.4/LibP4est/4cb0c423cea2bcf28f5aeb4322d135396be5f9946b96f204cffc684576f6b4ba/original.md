```
sc_list_destroy(list)
```

Destroy a linked list structure in O(N).

!!! note
    If allocator was provided in [`sc_list_new`](@ref), it will not be destroyed.


### Parameters

  * `list`:[in,out] All memory allocated for this list is freed.

### Prototype

```c
void sc_list_destroy (sc_list_t * list);
```
