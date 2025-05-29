```
project_body_field_to_2d_igrf(vec_body, igrf_nav, Cnb)
```

Project a body frame vector onto a 2D plane defined by the direction of the IGRF and a tangent vector to the Earth ellipsoid, which is computed by taking the cross product of the IGRF with the upward direction. Returns a 2D vector whose components describe the amount of the body field that is in alignment with the Earth field and an orthogonal direction to the Earth field (roughly to the east).

**Arguments:**

  * `vec_body`: vector in body frame (e.g., aircraft induced field)
  * `igrf_nav`: IGRF unit vector in navigation frame
  * `Cnb`:      `3` x `3` x `N` direction cosine matrix (body to navigation) [-]

**Returns:**

  * `v_out`: 2D vector whose components illustrate projection onto the Earth field and an orthogonal component
