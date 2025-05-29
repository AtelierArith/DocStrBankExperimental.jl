```
points(g::ICESat_Granule{:GLAH14}, step=1, bbox::Union{Nothing,Extent,NamedTuple} = nothing)
```

Retrieve the points for a given ICESat GLAH14 (Land Surface) granule as a list of namedtuples The names of the tuples are based on the following fields:

| Variable           | Original Field (in `Data_40HZ`) | Description                                 | Units                        |
|:------------------ |:------------------------------- |:------------------------------------------- |:---------------------------- |
| `longitude`        | `/Geolocation/d_lon`            | Longitude of segment center, WGS84, East=+  | decimal degrees              |
| `latitude`         | `Geolocation/d_lat`             | Latitude of segment center, WGS84, North=+  | decimal degrees              |
| `height`           | `Elevation_Surfaces/d_elev`     | + `Elevation_Corrections/d_satElevCorr`     | m above WGS84 ellipsoid      |
| `datetime`         | `DS_UTCTime_40`                 | Precise time of aquisiton                   | date-time                    |
| `quality` [^1]     | `Quality/elev_use_flg`          | & `Quality/sigma_att_flg` = 0               |                              |
|                    | & `Waveform/i_numPk` = 1        | & `Elevation_Corrections/d_satElevCorr` < 3 | 1=high quality               |
| `clouds`           | `Elevation_Flags/elv_cloud_flg` | Cloud contamination                         | -                            |
| `height_reference` | `Geophysical/d_DEM_elv`         | Height of the (best available) DEM          | height above WGS84           |
| `gain`             | `Waveform/i_gval_rcv`           | Gain value used for received pulse.         | -                            |
| `reflectivity`     | `Reflectivity/d_reflctUC`       | Reflectivity, not corrected                 | -                            |
| `attitude`         | `Quality/sigma_att_flg`         | Attitude quality indicator                  | 0=good; 50=warning; 100=bad; |
| `saturation`       | `Quality/sat_corr_flg`          | Saturation Correction Flag                  | 0=not_saturated;             |

You can get the output in a `DataFrame` with `DataFrame(points(g))`.

[^1]: Smith, B., Fricker, H. A., Gardner, A. S., Medley, B., Nilsson, J., Paolo, F. S., ... & Zwally, H. J. (2020). Pervasive ice sheet mass loss reflects competing ocean and atmosphere processes. Science, 368(6496), 1239-1242.
