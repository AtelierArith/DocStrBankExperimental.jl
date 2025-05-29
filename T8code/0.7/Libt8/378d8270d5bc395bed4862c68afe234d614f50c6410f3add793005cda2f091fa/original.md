```
t8_element_set_linear_id(ts, elem, level, id)
```

Initialize the entries of an allocated element according to a given linear id in a uniform refinement.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in,out] The element whose entries will be set.
  * `level`:[in] The level of the uniform refinement to consider.
  * `id`:[in] The linear id. id must fulfil 0 <= id < 'number of leaves in the uniform refinement'

### Prototype

```c
void t8_element_set_linear_id (const t8_eclass_scheme_c *ts, t8_element_t *elem, int level, t8_linearidx_t id);
```
