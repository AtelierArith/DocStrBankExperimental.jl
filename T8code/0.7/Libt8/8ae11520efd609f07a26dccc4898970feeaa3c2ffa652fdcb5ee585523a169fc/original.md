```
t8_cmesh_is_committed(cmesh)
```

Check whether a cmesh is not NULL, initialized and committed. In addition, it asserts that the cmesh is consistent as much as possible.

# Arguments

  * `cmesh`:[in] This cmesh is examined. May be NULL.

# Returns

True if cmesh is not NULL and t8*cmesh*init has been called on it as well as t8*cmesh*commit. False otherwise.

### Prototype

```c
int t8_cmesh_is_committed (const t8_cmesh_t cmesh);
```
