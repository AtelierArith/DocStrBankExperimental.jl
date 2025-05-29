```
t8_cmesh_treeid_is_ghost(cmesh, ltreeid)
```

Query whether a given [`t8_locidx_t`](@ref) belongs to a ghost of a cmesh.

# Arguments

  * `cmesh`:[in] The cmesh to be considered.
  * `ltreeid`:[in] An (possible) ghost index.

# Returns

True if *ltreeid* matches the range of ghost trees of *cmesh*. False if not. *cmesh* must be committed before calling this function.

### Prototype

```c
int t8_cmesh_treeid_is_ghost (const t8_cmesh_t cmesh, const t8_locidx_t ltreeid);
```
