```
points(g::ICESat2_Granule{:ATL08}; tracks=icesat2_tracks, step=1, canopy=false, ground=true, bbox::Union{Nothing,Extent,NamedTuple} = nothing)
```

Retrieve the points for a given ICESat-2 ATL08 (Land and Vegetation Height) granule as a list of namedtuples, one for each beam. With the `tracks` keyword, you can specify which tracks to include. The default is to include all tracks. With the `step` keyword, you can choose to limit the number of points, the default is 1 (all points). With setting `ground` and or `canopy`, you can control to include ground and/or canopy points. Finally, with the `ground_field` and `canopy_field` settings, you can determine the source field. The default is `h_te_mean` for ground and `h_mean_canopy_abs` for canopy. With the introduction of v5, a 20m resolution is also available for estimation, which you can enable with `highres`. Note that filtering with a bounding box doesn't yet work when `highres` is true.

The names of the tuples are based on the following fields:

| Column             | Field                                    | Description                                           | Units                        |
|:------------------ |:---------------------------------------- |:----------------------------------------------------- |:---------------------------- |
| `longitude`        | `land_segments/longitude`                | Longitude of segment center, WGS84, East=+            | decimal degrees              |
| `latitude`         | `land_segments/latitude`                 | Latitude of segment center, WGS84, North=+            | decimal degrees              |
| `height`           | `land_segments/terrain/h_te_mean`        | Standard land-ice segment height                      | m above the WGS 84 ellipsoid |
| `height_error`     | `land_segments/terrain/h_te_uncertainty` | Total vertical geolocation error                      | m                            |
| `datetime`         | `land_segments/delta_time`               | + `ancillary_data/atlas_sdp_gps_epoch` + `gps_offset` | date-time                    |
| `quality`          | `land_segments/terrain_flg`              | Boolean flag indicating the best-quality subset       | 1 = high quality             |
| `phr`              | `land_segments/ph_removal_flag`          | More than 50% of photons removed                      | -                            |
| `sensitivity`      | `land_segments/snr`                      | The signal to noise ratio                             | -                            |
| `scattered`        | `land_segments/msw_flag`                 | Multiple Scattering warning flag                      | -1=unknown; 0=none           |
| `saturated`        | `land_segments/sat_flag`                 | Saturation detected                                   | -                            |
| `clouds`           | `land_segments/layer_flag`               | Clouds or blowing snow are likely present             | -                            |
| `track`            | `gt1l` - `gt3r` groups                   | -                                                     | -                            |
| `strong_beam`      | `-`                                      | "strong" (true) or "weak" (false) laser power         | -                            |
| `classification`   | `-`                                      | "ground", "high_canopy"                               | -                            |
| `height_reference` | `land_segments/dem_h`                    | Height of the (best available) DEM                    | m above the WGS 84 ellipsoid |
| `detector_id`      | `atlas_spot_number attribute`            | -                                                     | -                            |

You can combine the output in a `DataFrame` with `reduce(vcat, DataFrame.(points(g)))` if you want to change the default arguments or just `DataFrame(g)` with the default options.
