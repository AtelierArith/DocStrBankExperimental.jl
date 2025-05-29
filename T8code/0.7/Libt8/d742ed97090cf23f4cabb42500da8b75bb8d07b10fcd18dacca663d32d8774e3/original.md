```
t8_element_shape(ts, elem)
```

Return the shape of an allocated element according its type. For example, a child of an element can be an element of a different shape and has to be handled differently - according to its shape.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The element to be considered

# Returns

The shape of the element as an eclass

### Prototype

```c
t8_element_shape_t t8_element_shape (const t8_eclass_scheme_c *ts, const t8_element_t *elem);
```
