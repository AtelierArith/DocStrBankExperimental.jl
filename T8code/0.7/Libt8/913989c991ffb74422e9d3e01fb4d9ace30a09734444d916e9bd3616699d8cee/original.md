```
t8_element_tree_face(ts, elem, face)
```

Given an element and a face of this element. If the face lies on the tree boundary, return the face number of the tree face. If not the return value is arbitrary.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The element.
  * `face`:[in] The index of a face of *elem*.

# Returns

The index of the tree face that *face* is a subface of, if *face* is on a tree boundary. Any arbitrary integer if *is* not at a tree boundary.

### Prototype

```c
int t8_element_tree_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face);
```
