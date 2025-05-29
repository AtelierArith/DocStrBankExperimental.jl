```
calc_course(velocityENU, elevation, azimuth, down_wind_direction = π/2, respos=true)
```

Calculate the course angle in radian.

  * velocityENU:         Kite velocity in EastNorthUp reference frame
  * down*wind*direction: The direction the wind is going to; zero at north;                      clockwise positive from above; default: going to east.
  * respos:              If true, the result is in the range 0 .. 2π, otherwis -π .. π
