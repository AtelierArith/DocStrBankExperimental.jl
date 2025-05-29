```
t8_plane_point_inside(point_on_face, face_normal, point)
```

Check if a point lays on the inner side of a plane of a bilinearly interpolated volume element.  the plane is described by a point and the normal of the face.

# Arguments

  * `point_on_face`:[in] A point on the plane
  * `face_normal`:[in] The normal of the face
  * `point`:[in] The point to check

# Returns

0 if the point is outside, 1 otherwise.

### Prototype

```c
int t8_plane_point_inside (const double point_on_face[3], const double face_normal[3], const double point[3]);
```
