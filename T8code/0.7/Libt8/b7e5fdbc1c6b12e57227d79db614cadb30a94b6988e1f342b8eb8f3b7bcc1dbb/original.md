```
t8_cmesh_is_empty(cmesh)
```

Check whether a cmesh is empty on all processes.

# Arguments

  * `cmesh`:[in] A committed cmesh.

# Returns

True (non-zero) if and only if the cmesh has trees at all.

### Prototype

```c
int t8_cmesh_is_empty (t8_cmesh_t cmesh);
```
