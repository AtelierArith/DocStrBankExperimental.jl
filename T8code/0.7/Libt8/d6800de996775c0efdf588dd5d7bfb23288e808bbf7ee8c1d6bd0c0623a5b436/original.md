```
t8_element_face_child_face(ts, elem, face, face_child)
```

Given a face of an element and a child number of a child of that face, return the face number of the child of the element that matches the child face.

```c++
  x ---- x   x      x           x ---- x
  |      |   |      |           |   |  | <-- f
  |      |   |      x           |   x--x
  |      |   |                  |      |
  x ---- x   x                  x ---- x
   elem    face  face_child    Returns the face number f
```

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The element.
  * `face`:[in] Then number of the face.
  * `face_child`:[in] A number 0 <= *face_child* < num_face_children, specifying a child of *elem* that shares a face with *face*. These children are counted in linear order. This coincides with the order of children from a call to t8*element*children*at*face.

# Returns

The face number of the face of a child of *elem* that coincides with *face_child*.

### Prototype

```c
int t8_element_face_child_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face, int face_child);
```
