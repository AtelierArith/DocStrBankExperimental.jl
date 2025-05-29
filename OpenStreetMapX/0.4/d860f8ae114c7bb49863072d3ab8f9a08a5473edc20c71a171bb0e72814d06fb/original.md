```
ENU(bounds::Bounds{LLA},
	lla_ref::LLA = center(bounds),
	datum::Ellipsoid = WGS84)
```

Convert LLA Bounds to ENU

there's not an unambiguous conversion, but for now, returning the minimum bounds that contain all points contained by the input bounds
