```
t8_element_get_linear_id(ts, elem, level)
```

Compute the linear id of a given element in a hypothetical uniform refinement of a given level.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The element whose id we compute.
  * `level`:[in] The level of the uniform refinement to consider.

# Returns

The linear id of the element.

### Prototype

```c
t8_linearidx_t t8_element_get_linear_id (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int level);
```
