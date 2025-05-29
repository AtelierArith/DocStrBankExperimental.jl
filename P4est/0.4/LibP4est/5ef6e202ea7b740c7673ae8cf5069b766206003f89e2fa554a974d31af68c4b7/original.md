```
sc_list_remove(list, pred)
```

Remove an element after a given list position.

### Parameters

  * `list`:[in,out] Valid, non-empty list object.
  * `pred`:[in] The predecessor of the element to be removed. If *pred* == NULL, the first element is removed, which is equivalent to calling [`sc_list_pop`](@ref) (list).

### Returns

The data of the removed and freed link.

### Prototype

```c
void *sc_list_remove (sc_list_t * list, sc_link_t * pred);
```
