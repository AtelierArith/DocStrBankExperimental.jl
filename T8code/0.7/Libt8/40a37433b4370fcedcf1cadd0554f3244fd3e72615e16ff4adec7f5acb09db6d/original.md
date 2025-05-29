```
t8_cmesh_treeid_is_local_tree(cmesh, ltreeid)
```

Query whether a given [`t8_locidx_t`](@ref) belongs to a local tree of a cmesh.

# Arguments

  * `cmesh`:[in] The cmesh to be considered.
  * `ltreeid`:[in] An (possible) tree index.

# Returns

True if *ltreeid* matches the range of local trees of *cmesh*. False if not. *cmesh* must be committed before calling this function.

### Prototype

```c
int t8_cmesh_treeid_is_local_tree (const t8_cmesh_t cmesh, const t8_locidx_t ltreeid);
```
