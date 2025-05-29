```
function ortho2inv(x, y, ϕ1, λ0)
```

Inverse stereo orthographic projection centered on (ϕ1, λ0). Given a point (x, y) on the plane, with x ∈ [-1, 1], y ∈ [-1, 1], return a 3-tuple of type (Bool, Number, Number). The boolean specifies if (x, y) falls within the map (true) or not (false), the second and third arguments are the latitude and longitude in radians.
