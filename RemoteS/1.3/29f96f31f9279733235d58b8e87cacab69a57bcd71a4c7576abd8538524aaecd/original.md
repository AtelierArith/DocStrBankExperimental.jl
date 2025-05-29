sat*scenes(track, sat*name::String)

Compute polygons delimiting AQUA and TERRA scenes.

  * `trac`: Is an orbit computed with `sat_tracks` at steps of 1 minute (crucial)
  * `sat_name`: The satellite name. At this time only AQUA and TERRA are allowed.

Returns a GMTdataset vector with the polygons and the scene names in the dataset `header` field.

# Example

Imagine that `orb` was obtained with

orb = sat_tracks(tle=[tle1; tle2], start=DateTime("2021-09-02T13:30:00"), 	stop=DateTime("2021-09-02T13:40:00"), step="1m");

The scenes limits (two) are computed with:

```
Dscenes = sat_scenes(orb, "AQUA");
```
