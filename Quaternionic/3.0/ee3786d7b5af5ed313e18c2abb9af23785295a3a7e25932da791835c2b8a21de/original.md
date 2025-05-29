```
from_spherical_coordinates(θ, ϕ)
```

Return a rotor corresponding to these spherical coordinates.

Considering (θ, ϕ) as a point $n̂$ on the sphere, we can also construct a quaternion that rotates the $z$ axis onto that point.  Here, we use the standard commonly used in physics: θ represents the "polar angle" between the $z$ axis and the direction $n̂$, while ϕ represents the "azimuthal angle" between the $x$ axis and the projection of $n̂$ into the $x$-$y$ plane. Both angles must be given in radians.
