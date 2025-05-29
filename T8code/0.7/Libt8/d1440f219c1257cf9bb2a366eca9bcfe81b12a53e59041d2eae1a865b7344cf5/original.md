```
t8_element_children_at_face(ts, elem, face, children, num_children, child_indices)
```

Given an element and a face of the element, compute all children of the element that touch the face.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The element.
  * `face`:[in] A face of *elem*.
  * `children`:[in,out] Allocated elements, in which the children of *elem* that share a face with *face* are stored. They will be stored in order of their linear id.
  * `num_children`:[in] The number of elements in *children*. Must match the number of children that touch *face*. t8*element*num*face*children
  * `child_indices`:[in,out] If not NULL, an array of num_children integers must be given, on output its i-th entry is the child_id of the i-th face_child. It is valid to call this function with elem = children[0].

### Prototype

```c
void t8_element_children_at_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face, t8_element_t *children[], int num_children, int *child_indices);
```
