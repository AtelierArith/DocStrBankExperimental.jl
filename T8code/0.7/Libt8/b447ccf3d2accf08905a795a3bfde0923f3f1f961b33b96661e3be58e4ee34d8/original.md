```
t8_element_last_descendant(ts, elem, desc, level)
```

Compute the last descendant of a given element.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The element whose descendant is computed.
  * `desc`:[out] The last element in a uniform refinement of *elem* of the maximum possible level.

### Prototype

```c
void t8_element_last_descendant (const t8_eclass_scheme_c *ts, const t8_element_t *elem, t8_element_t *desc, int level);
```
