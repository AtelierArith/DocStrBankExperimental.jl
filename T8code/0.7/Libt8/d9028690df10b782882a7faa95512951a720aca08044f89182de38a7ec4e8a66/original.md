```
t8_element_get_face_corner(ts, elem, face, corner)
```

Return the corner number of an element's face corner. Example quad: 2 x –- x 3 | | | | face 1 0 x –- x 1 Thus for face = 1 the output is: corner=0 : 1, corner=1: 3

The order in which the corners must be given is determined by the eclass of *element*: LINE/QUAD/TRIANGLE: No specific order. HEX : In Z-order of the face starting with the lowest corner number. TET : Starting with the lowest corner number counterclockwise as seen from 'outside' of the element.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `element`:[in] The element.
  * `face`:[in] A face index for *element*.
  * `corner`:[in] A corner index for the face 0 <= *corner* < num_face_corners.

# Returns

The corner number of the *corner*-th vertex of *face*.

### Prototype

```c
int t8_element_get_face_corner (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face, int corner);
```
