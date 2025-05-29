```
calc_orient_rot(x, y, z; viewer=false, ENU=true)
```

Calculate the rotation matrix based on the kite reference frame, by default  passed as ENU (east, north, up), or as NED (north, east, down) if ENU is false. If viewer is true, the rotation matrix is calculated based with respect to the viewer reference frame.
