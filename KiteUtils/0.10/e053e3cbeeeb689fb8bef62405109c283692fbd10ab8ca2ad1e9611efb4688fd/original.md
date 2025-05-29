```
calc_heading(orientation, elevation, azimuth; upwind_dir=-pi/2, respos=true)
```

Calculate the heading angle of the kite in radians. The heading is the direction the nose of the kite is pointing to. The orientation is given in Euler angles, calculated with respect to the North, East, Down reference frame. If respos is true the heading angle is defined in the range of 0 .. 2π, otherwise in the range -π .. π
