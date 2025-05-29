```
clip_orbits(track, BoundingBox::Vector{<:Real})
```

Clips the orbits that are contained inside a rectangular geographical region

  * `track`: A GMTdataset or a Mx2 matrix with the orbits [lon, lat] position. This is normally calculated   with the `sat_tracks` function.
  * `BoundingBox`: A vector the region limits made up with [lon*min, lon*max, lat*min, lat*max]

Returns a GMTdataset vector with the chunks of `tracks` that cross inside the `BoundingBox` region.

#Example Suppose `orb` holds orbits computed with sat_tracks() during 2 days, clip them inside the 20W-10E, 30N-45N window

```
D = clip_orbits(orb, [-20, 10, 30, 50]);
```
