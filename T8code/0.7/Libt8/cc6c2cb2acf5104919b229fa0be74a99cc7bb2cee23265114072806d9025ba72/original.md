```
t8_refcount_new()
```

Create a new reference counter with count initialized to 1. Equivalent to calling [`t8_refcount_init`](@ref) on a newly allocated refcount_t. It is mandatory to free this with t8*refcount*destroy.

# Returns

An allocated reference counter whose count has been set to one.

### Prototype

```c
t8_refcount_t * t8_refcount_new (void);
```
