```
ellipseinquad(qgon; action=:none)
ellipseinquad(qgon, action)
```

Calculate a Bézier-based ellipse that fits inside the quadrilateral `qgon`, an array with at least four Points that form a convex polygon, and add it to the current path.

It returns `ellipsecenter, ellipsesemimajor, ellipsesemiminor, ellipseangle`:

  * `ellipsecenter` the ellipse center
  * `ellipsesemimajor` ellipse semimajor axis
  * `ellipsesemiminor` ellipse semiminor axis
  * `ellipseangle` ellipse rotation

The function returns `O, 0, 0, 0` if a suitable ellipse can't be found. (The qgon is probably not a convex polygon.)

## Examples

```julia
ellipseinquad(box(O, 130, 130); action = :stroke)
```

```julia
ellipseinquad(box(O, 140, 230), :stroke)
```

### References

http://faculty.mae.carleton.ca/John_Hayes/Papers/InscribingEllipse.pdf
