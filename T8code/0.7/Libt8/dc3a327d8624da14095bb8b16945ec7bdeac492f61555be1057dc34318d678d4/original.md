```
t8_element_copy(ts, source, dest)
```

Copy all entries of **source** to **dest**. **dest** must be an existing element. No memory is allocated by this function.

!!! note
    *source* and *dest* may point to the same element.


# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `source`:[in] The element whose entries will be copied to **dest**.
  * `dest`:[in,out] This element's entries will be overwritten with the entries of **source**.

### Prototype

```c
void t8_element_copy (const t8_eclass_scheme_c *ts, const t8_element_t *source, t8_element_t *dest);
```
