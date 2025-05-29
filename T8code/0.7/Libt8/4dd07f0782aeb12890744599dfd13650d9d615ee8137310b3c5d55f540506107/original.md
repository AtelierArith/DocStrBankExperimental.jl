```
t8_geometry_type
```

This enumeration contains all possible geometries.

| Enumerator                           | Note                                                                                            |
|:------------------------------------ |:----------------------------------------------------------------------------------------------- |
| T8_GEOMETRY_TYPE_ZERO                | The zero geometry maps all points to zero.                                                      |
| T8_GEOMETRY_TYPE_LINEAR              | The linear geometry uses linear interpolations to interpolate between the tree vertices.        |
| T8_GEOMETRY_TYPE_LINEAR_AXIS_ALIGNED | The linear, axis aligned geometry uses only 2 vertices, since it is axis aligned.               |
| T8_GEOMETRY_TYPE_LAGRANGE            | The Lagrange geometry uses a mapping with Lagrange polynomials to approximate curved elements . |
| T8_GEOMETRY_TYPE_ANALYTIC            | The analytic geometry uses a user-defined analytic function to map into the physical domain.    |
| T8_GEOMETRY_TYPE_CAD                 | The opencascade geometry uses CAD shapes to map trees exactly to the underlying CAD model.      |
| T8_GEOMETRY_TYPE_COUNT               | This is no geometry type but can be used as the number of geometry types.                       |
| T8_GEOMETRY_TYPE_UNDEFINED           | This is no geometry type but is used for every geometry, where no type is defined               |
