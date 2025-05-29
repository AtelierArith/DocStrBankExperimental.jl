```
points(g::ICESat2_Granule{:ATL12}, tracks=icesat2_tracks)
```

Retrieve the points for a given ICESat-2 ATL12 (Ocean Surface Height) granule as a list of namedtuples, one for each beam. The names of the tuples are based on the following fields:

| Column        | Field                         | Description                                           | Units                        |
|:------------- |:----------------------------- |:----------------------------------------------------- |:---------------------------- |
| `longitude`   | `ssh_segments/longitude`      | Longitude of segment center, WGS84, East=+            | decimal degrees              |
| `latitude`    | `ssh_segments/latitude`       | Latitude of segment center, WGS84, North=+            | decimal degrees              |
| `height`      | `ssh_segments/heights/h`      | Standard land-ice segment height                      | m above the WGS 84 ellipsoid |
| `datetime`    | `ssh_segments/delta_time`     | + `ancillary_data/atlas_sdp_gps_epoch` + `gps_offset` | date-time                    |
| `track`       | `gt1l` - `gt3r` groups        | -                                                     | -                            |
| `strong_beam` | `-`                           | "strong" (true) or "weak" (false) laser power         | -                            |
| `detector_id` | `atlas_spot_number attribute` | -                                                     | -                            |

You can combine the output in a `DataFrame` with `reduce(vcat, DataFrame.(points(g)))` if you want to change the default arguments or `DataFrame(g)` with the default options.
