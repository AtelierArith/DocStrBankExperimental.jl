```
t8_element_num_siblings(ts, elem)
```

Compute the number of siblings of an element. That is the number of  Children of its parent.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The element.

# Returns

The number of siblings of *element*. Note that this number is >= 1, since we count the element itself as a sibling.

### Prototype

```c
int t8_element_num_siblings (const t8_eclass_scheme_c *ts, const t8_element_t *elem);
```
