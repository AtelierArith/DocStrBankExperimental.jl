```
EllipticalArc(c::VecTypes, r1::Real, r2::Real, angle::Real, a1::Real, a2::Real)
EllipticalArc(cx::Real, cy::Real, r1::Real, r2::Real, angle::Real, a1::Real, a2::Real)
```

A path command for use within a `BezierPath` which continues the current subpath with an elliptical arc. The ellipse is centered at `c` and has two radii, `r1` and `r2`, the orientation of which depends on `angle`.

If `angle == 0`, `r1` goes in x direction and `r2` in y direction. A positive `angle` in radians rotates the ellipse counterclockwise, and a negative `angle` clockwise.

The angles `a1` and `a2` are the start and stop positions of the arc on the ellipse. A value of `0` is where the radius `r1` points to, `pi/2` is where the radius `r2` points to, and so on. If `a2 > a1`, the arc turns counterclockwise. If `a1 > a2`, it turns clockwise.

If the last position of the subpath does not equal the start of the arc, the resulting path will have an implicit line segment between the two.
