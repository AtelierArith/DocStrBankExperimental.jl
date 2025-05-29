```
FV = rotate(FV::GMTfv, a=Float64[]; rx=0.0, ry=0.0, rz=0.0) -> GMTfv
```

Rotate the FacesVertices `FV` by the Euler angles (in degrees) `rx`, `ry` and `rz`.

The *insitu* version `rotate!()` does it in-place. Note: We set the `bfculling` value to false because after rotations surfaces are not guaranteed to be CCW.

### Args

  * `FV::GMTfv`: FacesVertices object
  * `a=[rx, ry, rz]`: Euler angles (in degrees) about the x, y and z axes.

### Kwargs

  * `rx, ry, rz`: Alternative to `a`, provide one to three of those Euler angles.
