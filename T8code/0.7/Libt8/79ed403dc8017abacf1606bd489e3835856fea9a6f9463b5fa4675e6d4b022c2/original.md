```
t8_element_child(ts, elem, childid, child)
```

Construct the child element of a given number.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] This must be a valid element, bigger than maxlevel.
  * `childid`:[in] The number of the child to construct.
  * `child`:[in,out] The storage for this element must exist. On output, a valid element. It is valid to call this function with elem = child.

### Prototype

```c
void t8_element_child (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int childid, t8_element_t *child);
```
