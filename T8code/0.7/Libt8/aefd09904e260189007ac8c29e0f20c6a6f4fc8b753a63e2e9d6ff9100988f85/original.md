```
t8_cmesh_is_initialized(cmesh)
```

Check whether a cmesh is not NULL, initialized and not committed. In addition, it asserts that the cmesh is consistent as much as possible.

# Arguments

  * `cmesh`:[in] This cmesh is examined. May be NULL.

# Returns

True if cmesh is not NULL, t8*cmesh*init has been called on it, but not t8*cmesh*commit. False otherwise.

### Prototype

```c
int t8_cmesh_is_initialized (t8_cmesh_t cmesh);
```
