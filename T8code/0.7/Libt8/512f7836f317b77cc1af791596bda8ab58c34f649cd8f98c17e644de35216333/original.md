```
t8_element_get_corner_face(ts, elem, corner, face)
```

Compute the face numbers of the faces sharing an element's corner. Example quad: 2 x –- x 3 | | | | face 1 0 x –- x 1 face 2 Thus for corner = 1 the output is: face=0 : 2, face=1: 1

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `element`:[in] The element.
  * `corner`:[in] A corner index for the face.
  * `face`:[in] A face index for *corner*.

# Returns

The face number of the *face*-th face at *corner*.

### Prototype

```c
int t8_element_get_corner_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int corner, int face);
```
