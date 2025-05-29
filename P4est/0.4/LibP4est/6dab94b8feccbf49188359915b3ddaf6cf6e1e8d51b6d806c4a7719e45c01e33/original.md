```
sc_hash_unlink_destroy(hash)
```

Same effect as unlink and destroy, but in O(1). This is dangerous because of potential memory leaks.

### Parameters

  * `hash`:[in] Hash structure to be unlinked and destroyed.

### Prototype

```c
void sc_hash_unlink_destroy (sc_hash_t * hash);
```
