```
Ellipsoid(c::Vec, r::Vec, dir::Vec, open::Float64)

An ellipsoid with a center, `c`, and radii, `r`, as well as a direction (gets automatically normalized), `dir`, and an opening angle, `open`, creating a dome (or window), that the ellipsoid is defined in. Note that `open` is the angle between the dome's edge and the direction of the dome (so actually half the opening angle) and is defined in **some angular units** (using UnitfulAngles, for example: u"°").
```

`Ellipsoid` has 6 additional fields all relating to various spatial transformations that convert the ellipsoid to a unit-sphere and back again. These are all `CoordinateTransformations`.

# Examples

For an ellipsoid upwards-pointing hemisphere with a center at (1,2,3), and radii (4,5,6):

```jldoctest
julia> Ellipsoid(Vec(1,2,3), Vec(4,5,6), Vec(0,0,1), 0.0)
Rayden.Ellipsoid([1.0, 2.0, 3.0], [4.0, 5.0, 6.0], [0.0, 0.0, 1.0], 0.0, Translation(-1.0, -2.0, -3.0), LinearMap([0.25 0.0 0.0; 0.0 0.2 0.0; 0.0 0.0 0.166667]), AffineMap([0.25 0.0 0.0; 0.0 0.2 0.0; 0.0 0.0 0.166667], [-0.25, -0.4, -0.5]), Translation(1.0, 2.0, 3.0), LinearMap([4.0 0.0 0.0; 0.0 5.0 0.0; 0.0 0.0 6.0]), AffineMap([4.0 0.0 0.0; 0.0 5.0 0.0; 0.0 0.0 6.0], [1.0, 2.0, 3.0]))
```
