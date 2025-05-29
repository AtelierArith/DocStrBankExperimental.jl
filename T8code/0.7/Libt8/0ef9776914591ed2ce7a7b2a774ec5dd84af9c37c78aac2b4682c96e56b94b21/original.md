```
t8_refcount_init(rc)
```

Initialize a reference counter to 1. It is legal if its status prior to this call is undefined.

# Arguments

  * `rc`:[out] The reference counter is set to one by this call.

### Prototype

```c
void t8_refcount_init (t8_refcount_t *rc);
```
