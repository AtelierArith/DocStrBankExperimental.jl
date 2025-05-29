`Ellipsoid{T}` represented by 

  * `c` the center
  * `sx, sy, sz` semi-axes. They should be orthogonal but this not checked at the construction.

The type `T` is the promote type of the entry types of `c, sx, sy, sz`.

**Example**

```
Ellipsoid([0,0,0], [1,0,0], [0,0.5,0], [0,0,0.1])
```
