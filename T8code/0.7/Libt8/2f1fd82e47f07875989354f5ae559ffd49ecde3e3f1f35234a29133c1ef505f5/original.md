```
t8_element_is_family(ts, fam)
```

Query whether a given set of elements is a family or not.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `fam`:[in] An array of as many elements as an element of class **ts** has children.

# Returns

Zero if **fam** is not a family, nonzero if it is.

### Prototype

```c
int t8_element_is_family (const t8_eclass_scheme_c *ts, t8_element_t *const *fam);
```
