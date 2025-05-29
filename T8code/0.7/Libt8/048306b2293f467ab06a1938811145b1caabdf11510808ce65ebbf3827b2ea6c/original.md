```
t8_cmesh_set_derive(cmesh, set_from)
```

This function sets a cmesh to be derived from. The default is to create a cmesh standalone by specifying all data manually. A coarse mesh can also be constructed by deriving it from an existing one. The derivation from another cmesh may optionally be combined with a repartition or uniform refinement of each tree. This function overrides a previously set cmesh to be derived from.

# Arguments

  * `cmesh`:[in,out] Must be initialized, but not committed. May even be NULL to revert to standalone.
  * `set_from`:[in,out] Reference counter on this cmesh is bumped. It will be unbumped by t8*cmesh*commit, after which *from* is no longer remembered. Other than that the from object is not changed.

### Prototype

```c
void t8_cmesh_set_derive (t8_cmesh_t cmesh, t8_cmesh_t set_from);
```
