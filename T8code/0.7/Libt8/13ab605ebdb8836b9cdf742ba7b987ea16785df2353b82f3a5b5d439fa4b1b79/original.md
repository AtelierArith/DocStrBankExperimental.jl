```
t8_element_compare(ts, elem1, elem2)
```

Compare two elements with respect to the scheme.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem1`:[in] The first element.
  * `elem2`:[in] The second element.

# Returns

negative if elem1 < elem2, zero if elem1 equals elem2 and positive if elem1 > elem2. If elem2 is a copy of elem1 then the elements are equal.

### Prototype

```c
int t8_element_compare (const t8_eclass_scheme_c *ts, const t8_element_t *elem1, const t8_element_t *elem2);
```
