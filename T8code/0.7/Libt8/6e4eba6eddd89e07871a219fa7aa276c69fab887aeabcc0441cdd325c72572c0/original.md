```
t8_element_ancestor_id(ts, elem, level)
```

Compute the ancestor id of an element, that is the child id at a given level.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] This must be a valid element.
  * `level`:[in] A refinement level. Must satisfy *level* < elem.level

# Returns

The child_id of *elem* in regard to its *level* ancestor.

### Prototype

```c
int t8_element_ancestor_id (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int level);
```
