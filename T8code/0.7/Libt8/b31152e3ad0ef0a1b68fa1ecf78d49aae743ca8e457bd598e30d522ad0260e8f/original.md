```
t8_eclass
```

This enumeration contains all possible element classes.

| Enumerator         | Note                                                                                                              |
|:------------------ |:----------------------------------------------------------------------------------------------------------------- |
| T8_ECLASS_VERTEX   | The vertex is the only zero-dimensional element class.                                                            |
| T8_ECLASS_LINE     | The line is the only one-dimensional element class.                                                               |
| T8_ECLASS_QUAD     | The quadrilateral is one of two element classes in two dimensions.                                                |
| T8_ECLASS_TRIANGLE | The element class for a triangle.                                                                                 |
| T8_ECLASS_HEX      | The hexahedron is one three-dimensional element class.                                                            |
| T8_ECLASS_TET      | The tetrahedron is another three-dimensional element class.                                                       |
| T8_ECLASS_PRISM    | The prism has five sides: two opposing triangles joined by three quadrilaterals.                                  |
| T8_ECLASS_PYRAMID  | The pyramid has a quadrilateral as base and four triangles as sides.                                              |
| T8_ECLASS_COUNT    | This is no element class but can be used as the number of element classes.                                        |
| T8_ECLASS_INVALID  | This is no element class but can be used for the case a class of a third party library is not supported by t8code |
