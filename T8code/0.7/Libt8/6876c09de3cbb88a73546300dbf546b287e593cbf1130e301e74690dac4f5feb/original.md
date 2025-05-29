```
t8_element_parent(ts, elem, parent)
```

Compute the parent of a given element **elem** and store it in **parent**. **parent** needs to be an existing element. No memory is allocated by this function. **elem** and **parent** can point to the same element, then the entries of **elem** are overwritten by the ones of its parent.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The element whose parent will be computed.
  * `parent`:[in,out] This element's entries will be overwritten by those of **elem**'s parent. The storage for this element must exist and match the element class of the parent.

### Prototype

```c
void t8_element_parent (const t8_eclass_scheme_c *ts, const t8_element_t *elem, t8_element_t *parent);
```
