```
t8_vec_tri_normal(p1, p2, p3, normal)
```

Compute the normal of a triangle given by its three vertices.

# Arguments

  * `p1`:[in] A 3D vector.
  * `p2`:[in] A 3D vector.
  * `p3`:[in] A 3D vector.
  * `Normal`:[out] vector of the triangle. (Not necessarily of length 1!)

### Prototype

```c
static inline void t8_vec_tri_normal (const double p1[3], const double p2[3], const double p3[3], double normal[3]);
```
