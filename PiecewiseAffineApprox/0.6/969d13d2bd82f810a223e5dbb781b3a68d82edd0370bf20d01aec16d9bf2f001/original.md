```
PWAFunc{C<:Curvature,D}
```

A piecewise linear function that can be either convex and concave represented by a set of (hyper)planes.

If the curvature of the function is convex, the piecewise linear Function is defined as the pointwise maximum over the planes. A concave pwa function is handled by storing its negative and negating when evaluting.
