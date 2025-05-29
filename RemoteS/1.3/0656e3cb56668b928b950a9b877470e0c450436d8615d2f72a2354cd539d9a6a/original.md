```
sat_tracks(; geocentric::Bool=false, tiles::Bool=false, position::Bool=false, kwargs...)
```

Compute satellite tracks using the TLE, or Two Line Elements set, a data format that contains information about the orbit at a specific epoch of an Earth-orbiting object. It can also calculate polygons arround the scene extents of AQUA and TERRA satellites as well as create the scene names, which provides a mean to direct download that data.

  * `start`: A DateTime object or a string convertable to a DateTime with `DateTime(start)`  specifying the start of the orbit calculation. If omited, current time in UTC will be used.
  * `duration`: Length of time for which the orbit is calculated. Accepts duration in days, hours,  minutes or seconds. The default is minutes (100 minutes). To use other units use a string with  the value appended with 'D', 'h', 'm' or 's'. *e.g.* `duration="55m"` to compute orbit 55 minutes from `start`
  * `step` or `inc` or `dt`: The time interval at which to compute locations along the orbit. The default  unit here is seconds (30 sec) but minutes can be used as well by appending 'm'. *e.g.* `step="1m"`
  * `stop`: As alternative to `duration` provide the end date for the orbit. Same conditions as `start`
  * `position`: Computes only first location at the `start` time. Boolean, use `position=true`
  * `geocentric`: Boolean to controls if output is `lon,lat,alt,time` (the default) or `ECEF` coordinates + time.
  * `tle` or `TLE`: a file name with the TLE data for a specific satellite and period. It can also be a two elements string vector with the first and second lines of the TLE file.
  * `tiles`: Compute the scene limits and file names for some satellites. Currently AQUA only.
  * `sat`, `SAT` or `satellite`: Name of the satellite to use; choose from (string or symbols)  :TERRA, :AQUA. Use only with the `tiles` option.

### Returns

A GMTdataset with the orbit or the scene polygons

## Example:

Compute ~one orbit of the AQUA satellite starting at current local time. Note, this will be accurate for the month of September 2021. For other dates it needs an updated TLE.

```
tle1 = "1 27424U 02022A   21245.83760660  .00000135  00000-0  39999-4 0  9997";
tle2 = "2 27424  98.2123 186.0654 0002229  67.6025 313.3829 14.57107527 28342";
orb = sat_tracks(tle=[tle1; tle2], duration=100);
```

and the orbit track can be visualized with

```
imshow(orb,  proj=:Robinson, region=:global, coast=true)
```

WARNING: This function depends on the SatelliteToolbox extension that is not loaded by default. Load it with:

  * $using RemoteS, SatelliteToolboxTle, SatelliteToolboxPropagators, SatelliteToolboxTransformations$
