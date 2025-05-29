ray2raydist -  Minimum distance between two 3D rays

```
Usage: d = ray2raydist(p1, v1, p2, v2)

Arguments:
      p1, p2 - 3D points that lie on rays 1 and 2.
      v1, v2 - 3D vectors defining the direction of each ray.

Returns:
           d - The minimum distance between the rays.
```

Each ray is defined by a point on the ray and a vector giving the direction of the ray.  Thus a point on ray 1 will be given by  p1 + alpha*v1  where alpha is some scalar.
