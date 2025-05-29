```
t8_cmesh_is_equal(cmesh_a, cmesh_b)
```

Check whether two given cmeshes carry the same information.

# Arguments

  * `cmesh_a`:[in] The first of the two cmeshes to be checked.
  * `cmesh_b`:[in] The second of the two cmeshes to be checked.

# Returns

True if both cmeshes carry the same information, false otherwise. TODO: define carefully. Orders, sequences, equivalences? This function works on committed and uncommitted cmeshes.

### Prototype

```c
int t8_cmesh_is_equal (t8_cmesh_t cmesh_a, t8_cmesh_t cmesh_b);
```
