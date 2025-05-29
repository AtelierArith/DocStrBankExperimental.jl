```
sc_list_reset(list)
```

Remove all elements from a list in O(N).

!!! note
    Calling [`sc_list_init`](@ref), then any list operations, then [`sc_list_reset`](@ref) is memory neutral.


### Parameters

  * `list`:[in,out] List structure to be emptied.

### Prototype

```c
void sc_list_reset (sc_list_t * list);
```
