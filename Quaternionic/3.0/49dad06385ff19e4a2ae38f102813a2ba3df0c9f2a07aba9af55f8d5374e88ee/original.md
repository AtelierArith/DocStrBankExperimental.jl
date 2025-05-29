```
to_spherical_coordinates(q)
```

Return the spherical coordinates corresponding to this quaternion.

We can treat the quaternion as a transformation taking the $z$ axis to some direction $n̂$.  This direction can be described in terms of spherical coordinates (θ, ϕ).  Here, we use the standard commonly used in physics: θ represents the "polar angle" between the $z$ axis and the direction $n̂$, while ϕ represents the "azimuthal angle" between the $x$ axis and the projection of $n̂$ into the $x$-$y$ plane.  Both angles are given in radians.
