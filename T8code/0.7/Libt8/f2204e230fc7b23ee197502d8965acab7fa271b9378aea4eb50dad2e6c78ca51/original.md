```
t8_element_sibling(ts, elem, sibid, sibling)
```

Compute a specific sibling of a given element **elem** and store it in **sibling**. **sibling** needs to be an existing element. No memory is allocated by this function. **elem** and **sibling** can point to the same element, then the entries of **elem** are overwritten by the ones of its i-th sibling.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The element whose sibling will be computed.
  * `sibid`:[in] The id of the sibling computed.
  * `sibling`:[in,out] This element's entries will be overwritten by those of **elem**'s sibid-th sibling. The storage for this element must exist and match the element class of the sibling.

### Prototype

```c
void t8_element_sibling (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int sibid, t8_element_t *sibling);
```
