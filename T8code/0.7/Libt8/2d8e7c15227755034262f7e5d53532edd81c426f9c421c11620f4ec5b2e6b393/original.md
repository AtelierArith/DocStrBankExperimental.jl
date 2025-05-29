```
t8_element_nca(ts, elem1, elem2, nca)
```

Compute the nearest common ancestor of two elements. That is, the element with highest level that still has both given elements as descendants.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem1`:[in] The first of the two input elements.
  * `elem2`:[in] The second of the two input elements.
  * `nca`:[in,out] The storage for this element must exist and match the element class of the child. On output the unique nearest common ancestor of **elem1** and **elem2**.

### Prototype

```c
void t8_element_nca (const t8_eclass_scheme_c *ts, const t8_element_t *elem1, const t8_element_t *elem2, t8_element_t *nca);
```
