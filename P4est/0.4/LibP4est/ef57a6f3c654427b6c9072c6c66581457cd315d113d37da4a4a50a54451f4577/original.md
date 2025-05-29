```
sc_list_unlink(list)
```

Unlink all list elements without returning them to the mempool. This runs in O(1) but is dangerous because the link memory stays alive.

### Parameters

  * `list`:[in,out] List structure to be unlinked.

### Prototype

```c
void sc_list_unlink (sc_list_t * list);
```
