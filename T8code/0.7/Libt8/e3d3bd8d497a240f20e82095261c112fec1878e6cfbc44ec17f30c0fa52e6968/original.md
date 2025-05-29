```
t8_geom_get_scaling_factor_face_through_volume_prism(face, ref_coords)
```

Calculates the scaling factor for the displacement of an face through the volume of a prism element.

# Arguments

  * `face_index`:[in] Index of the displaced face.
  * `ref_coords`:[in] Array containing the coordinates of the reference point.

# Returns

The scaling factor of the face displacement at the point of the reference coordinates inside the prism volume.

### Prototype

```c
double t8_geom_get_scaling_factor_face_through_volume_prism (const int face, const double *ref_coords);
```
