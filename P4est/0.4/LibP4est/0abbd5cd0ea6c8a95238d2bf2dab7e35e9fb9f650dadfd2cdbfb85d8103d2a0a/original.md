```
sc_hash_foreach(hash, fn)
```

Invoke a callback for every member of the hash table. The functions hash_fn and equal_fn are not called by this function.

### Prototype

```c
void sc_hash_foreach (sc_hash_t * hash, sc_hash_foreach_t fn);
```
