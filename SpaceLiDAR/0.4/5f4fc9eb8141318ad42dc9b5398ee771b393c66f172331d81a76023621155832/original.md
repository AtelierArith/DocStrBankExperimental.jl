```
points(g::ICESat2_Granule{:ATL03}, tracks=icesat2_tracks; step=1, bbox::Union{Nothing,Extent,NamedTuple} = nothing)
```

Retrieve the points for a given ICESat-2 ATL03 (Global Geolocated Photon Data) granule as a list of namedtuples, one for each beam. The names of the tuples are based on the following fields:

| Column             | Field                         | Description                                           | Units                        |
|:------------------ |:----------------------------- |:----------------------------------------------------- |:---------------------------- |
| `longitude`        | `heights/lon_ph`              | Longitude of photon, WGS84, East=+                    | decimal degrees              |
| `latitude`         | `heights/lat_ph`              | Latitude of photon, WGS84, North=+                    | decimal degrees              |
| `height`           | `heights/h_ph`                | Photon WGS84 Height                                   | m above the WGS 84 ellipsoid |
| `quality`          | `heights/quality_ph`          | Indicates the quality of the associated photon        | 0 = nominal                  |
| `uncertainty`      | `geolocation/sigma_h`         | Estimated height uncertainty                          | m                            |
| `datetime`         | `heights/delta_time`          | + `ancillary_data/atlas_sdp_gps_epoch` + `gps_offset` | date-time                    |
| `confidence`       | `heights/signal_conf_ph`      | Photon Signal Confidence                              | 2=low; 3=med; 4=high         |
| `segment`          | `geolocation/segment_id`      | Along-track segment ID number                         | -                            |
| `track`            | `gt1l` - `gt3r` groups        | -                                                     | -                            |
| `strong_beam`      | `-`                           | "strong" (true) or "weak" (false) laser power         | -                            |
| `sun_angle`        | `geolocation/solar_elevation` | Sun angle                                             | ° above horizon              |
| `detector_id`      | `atlas_spot_number attribute` | -                                                     | -                            |
| `height_reference` | `heights/dem/dem_h`           | Height of the (best available) DEM                    | m above the WGS 84 ellipsoid |

You can combine the output in a `DataFrame` with `reduce(vcat, DataFrame.(points(g)))` if you want to change the default arguments or `DataFrame(g)` with the default options.
