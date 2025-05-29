```
t8_element_count_leaves_from_root(ts, level)
```

Count how many leaf descendants of a given uniform level the root element will produce.

This is a convenience function, and can be implemented via t8*element*count_leaves.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `level`:[in] A refinement level.

# Returns

The value of t8*element*count_leaves if the input element is the root (level 0) element.

### Prototype

```c
t8_gloidx_t t8_element_count_leaves_from_root (const t8_eclass_scheme_c *ts, int level);
```
