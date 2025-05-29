```
t8_refcount_destroy(rc)
```

Destroy a reference counter that we allocated with t8*refcount*new. Its reference count must have decreased to zero.

# Arguments

  * `rc`:[in,out] Allocated, formerly valid reference counter.

### Prototype

```c
void t8_refcount_destroy (t8_refcount_t *rc);
```
