```
t8_element_successor(ts, elem1, elem2)
```

Construct the successor in a uniform refinement of a given element.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem1`:[in] The element whose successor should be constructed.
  * `elem2`:[in,out] The element whose entries will be set.
  * `level`:[in] The level of the uniform refinement to consider.

### Prototype

```c
void t8_element_successor (const t8_eclass_scheme_c *ts, const t8_element_t *elem1, t8_element_t *elem2);
```
