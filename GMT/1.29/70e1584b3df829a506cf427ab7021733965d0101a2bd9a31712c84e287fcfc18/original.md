```
dist, az1, az2 = invgeod(lonlat1::Vector{<:Real}, lonlat2::Vector{<:Real}; proj::String="",
                         s_srs::String="", epsg::Integer=0, backward=false)
```

Solve the inverse geodesic problem.

Args:

  * `lonlat1`:  - coordinates of point 1 in the given projection (or a matrix with several points).
  * `lonlat2`:  - coordinates of point 2 in the given projection (or a matrix with same size as `lonlat1`).
  * `proj` or `s_srs`:  - the given projection whose ellipsoid we move along. Can be a proj4 string or an WKT.
  * `epsg`:     - Alternative way of specifying the projection [Default is WGS84].
  * `backward`: - If `true`, return backard azimuths.

### Returns

dist - A scalar with the distance between point 1 and point 2 (meters). Or a vector when lonlat1|2        have more than one pair of points. 

az1 - azimuth at point 1 (degrees) ∈ [-180, 180)

az2 - (forward) azimuth at point 2 (degrees) ∈ [-180, 180)

Remarks:

If either point is at a pole, the azimuth is defined by keeping the longitude fixed, writing lat = 90 +/- eps, and taking the limit as eps -> 0+.
