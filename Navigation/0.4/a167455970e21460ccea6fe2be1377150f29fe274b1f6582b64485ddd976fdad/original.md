```
destination_point(start_pos::Point, distance::Float64, bearing::Float64[,
 radius::Float64=Rₑ_m])
```

Given a `start_pos` [deg], initial `bearing` (clockwise from North) [deg], `distance` [m], and the earth `radius` [m] calculate the `destina­tion_point` [deg] travelling along a (shortest distance) great circle arc. (The distance must use the same radius as the radius of the earth.)

Source: www.movable-type.co.uk/scripts/latlong.html
