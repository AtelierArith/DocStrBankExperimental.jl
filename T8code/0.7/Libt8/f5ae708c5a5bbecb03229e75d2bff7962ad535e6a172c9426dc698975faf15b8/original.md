```
t8_element_count_leaves(ts, t, level)
```

Count how many leaf descendants of a given uniform level an element would produce.

Example: If *t* is a line element that refines into 2 line elements on each level, then the return value is max(0, 2^{*level* - level(*t*)}). Thus, if *t*'s level is 0, and *level* = 3, the return value is 2^3 = 8.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `t`:[in] The element to be checked.
  * `level`:[in] A refinement level.

# Returns

Suppose *t* is uniformly refined up to level *level*. The return value is the resulting number of elements (of the given level). If *level* < [`t8_element_level`](@ref)(t), the return value should be 0.

### Prototype

```c
t8_gloidx_t t8_element_count_leaves (const t8_eclass_scheme_c *ts, const t8_element_t *t, int level);
```
