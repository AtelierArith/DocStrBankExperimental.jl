```
t8_cmesh_set_partition_uniform(cmesh, element_level, ts)
```

Declare if a derived cmesh should be partitioned according to a uniform refinement of a given level for the provided scheme. This call is only valid when the cmesh is not yet committed via a call to t8*cmesh*commit and when the cmesh will be derived.

# Arguments

  * `cmesh`:[in,out] The cmesh to be updated.
  * `element_level`:[in] The refinement_level.
  * `ts`:[in] The element scheme describing the refinement pattern. We take ownership. This can be prevented by referencing **ts** before calling this function.

### Prototype

```c
void t8_cmesh_set_partition_uniform (t8_cmesh_t cmesh, int element_level, t8_scheme_cxx_t *ts);
```
