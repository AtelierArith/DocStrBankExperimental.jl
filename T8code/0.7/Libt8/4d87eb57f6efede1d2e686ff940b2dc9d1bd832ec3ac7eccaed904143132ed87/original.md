```
t8_geom_get_tet_face_intersection(face_index, ref_coords, face_intersection)
```

Calculates the face intersection of a ray passing trough the reference coordinates and the opposite vertex of that face for a tetrahedron. The coordinates of the face intersection are reference coordinates: [0,1]^3.

# Arguments

  * `face_index`:[in] Index of the face, on which the intersection should be calculated.
  * `ref_coords`:[in] Array containing the coordinates of the reference point.
  * `face_intersection`:[out] Three dimensional array containing the intersection point on the face in reference space.

### Prototype

```c
void t8_geom_get_tet_face_intersection (const int face_index, const double *ref_coords, double face_intersection[3]);
```
