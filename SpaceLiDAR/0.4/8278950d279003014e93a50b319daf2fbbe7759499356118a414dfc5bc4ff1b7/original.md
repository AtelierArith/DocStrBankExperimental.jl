```
points(g::ICESat2_Granule{:ATL06}, tracks=icesat2_tracks, step=1, bbox::Union{Nothing,Extent,NamedTuple} = nothing)
```

Retrieve the points for a given ICESat-2 ATL06 (Land Ice) granule as a list of namedtuples, one for each beam. The names of the tuples are based on the following fields:

| Column             | Field                                     | Description                                           | Units                        |
|:------------------ |:----------------------------------------- |:----------------------------------------------------- |:---------------------------- |
| `longitude`        | `land_ice_segments/longitude`             | Longitude of segment center, WGS84, East=+            | decimal degrees              |
| `latitude`         | `land_ice_segments/latitude`              | Latitude of segment center, WGS84, North=+            | decimal degrees              |
| `height`           | `land_ice_segments/h_li`                  | Standard land-ice segment height                      | m above the WGS 84 ellipsoid |
| `height_error`     | √(`land_ice_segments/sigma_geo_h`² +      | Total vertical geolocation error                      | m above the WGS 84 ellipsoid |
|                    | `land_ice_segments/h_li_sigma`²)          |                                                       |                              |
| `datetime`         | `land_ice_segments/delta_time`            | + `ancillary_data/atlas_sdp_gps_epoch` + `gps_offset` | date-time                    |
| `quality`          | `land_ice_segments/atl06_quality_summary` | Boolean flag indicating the best-quality subset       | 1 = high quality             |
| `track`            | `gt1l` - `gt3r` groups                    | -                                                     | -                            |
| `strong_beam`      | `-`                                       | "strong" (true) or "weak" (false) laser power         | -                            |
| `detector_id`      | `atlas_spot_number attribute`             | -                                                     | -                            |
| `height_reference` | `land_ice_segments/dem/dem_h`             | Height of the (best available) DEM                    | -                            |

You can combine the output in a `DataFrame` with `reduce(vcat, DataFrame.(points(g)))` if you want to change the default arguments or `DataFrame(g)` with the default options.
