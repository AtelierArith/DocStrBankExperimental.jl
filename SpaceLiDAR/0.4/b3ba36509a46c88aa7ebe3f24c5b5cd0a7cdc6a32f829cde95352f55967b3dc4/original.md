```
points(g::ICESat_Granule{:GLAH06}, step=1, bbox::Union{Nothing,Extent,NamedTuple} = nothing)
```

Retrieve the points for a given ICESat GLAH06 (Land Ice) granule as a list of namedtuples The names of the tuples are based on the following fields:

| Variable           | Original Field                        | Description                                           | Units                   |
|:------------------ |:------------------------------------- |:----------------------------------------------------- |:----------------------- |
| `longitude`        | `Data_40HZ/Geolocation/d_lon`         | Longitude of segment center, WGS84, East=+            | decimal degrees         |
| `latitude`         | `Data_40HZ/Geolocation/d_lat`         | Latitude of segment center, WGS84, North=+            | decimal degrees         |
| `height`           | `Data_40HZ/Elevation_Surfaces/d_elev` | + `Data_40HZ/Elevation_Corrections/d_satElevCorr`     | m above WGS84 ellipsoid |
| `datetime`         | `Data_40HZ/DS_UTCTime_40`             | Precise time of aquisiton                             | date-time               |
| `quality` [^1]     | `Data_40HZ/Quality/elev_use_flg`      | & `Data_40HZ/Quality/sigma_att_flg` = 0               |                         |
|                    | & `Data_40HZ/Waveform/i_numPk` = 1    | & `Data_40HZ/Elevation_Corrections/d_satElevCorr` < 3 | 1 = high quality        |
| `height_reference` | `land_ice_segments/dem/dem_h`         | Height of the (best available) DEM                    | height above WGS84      |

You can get the output in a `DataFrame` with `DataFrame(points(g))`.

[^1]: Smith, B., Fricker, H. A., Gardner, A. S., Medley, B., Nilsson, J., Paolo, F. S., ... & Zwally, H. J. (2020). Pervasive ice sheet mass loss reflects competing ocean and atmosphere processes. Science, 368(6496), 1239-1242.
