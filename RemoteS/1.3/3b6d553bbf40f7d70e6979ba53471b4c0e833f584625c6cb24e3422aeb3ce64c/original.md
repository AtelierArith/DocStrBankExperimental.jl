```
findscenes(lon::Real, lat::Real; kwargs...)
```

Find the names of the scenes that cover the location point `lon`, `lat` in the period determined by the dates and satellite set via kwargs.

  * `day`: Search only on the day time part of the orbits.
  * `night`: Search only on the night time part of the orbits.
  * `oc`: For the AQUA or TERRA satellites pick only the chlorophyl content scenes.
  * `sst`: For the AQUA or TERRA satellites pick only the Sae Surface Temperature content scenes.
  * `sat`, `SAT` or `satellite`: Name of the satellite to use; choose from (string or symbols)  :TERRA, :AQUA
  * `start`: A DateTime object or a string convertable to a DateTime with `DateTime(start)`  specifying the start of the looking period. If omited, current time in UTC will be used.
  * `duration`: Length of time for which the scenes are searched. The duration is expected in days  and can be a negative number, meaning we'll look that span days from `start`.
  * `stop`: As alternative to `duration` provide the end date for the serch. Same conditions as `start`
  * `tle` or `TLE`: a file name with the TLE data for a specific satellite and period. It can also be a two elements string vector with the first and second lines of the TLE file.

### Returns

A string vector with the scene names

## Example:

Find the AQUA scenes with chlorophyl-a (oceancolor) that cover the point (-8, 36) in the two days before "2021-09-07T17:00:00" Note, this will be accurate for the month of September 2021. For other dates it needs an updated TLE.

```
tle1 = "1 27424U 02022A   21245.83760660  .00000135  00000-0  39999-4 0  9997";
tle2 = "2 27424  98.2123 186.0654 0002229  67.6025 313.3829 14.57107527 28342";
findscenes(-8,36, start="2021-09-07T17:00:00", sat=:aqua, day=true, duration=-2, oc=1, tle=[tle1, tle2])

2-element Vector{String}:
"A2021251125500.L2_LAC_OC.nc"
"A2021252134000.L2_LAC_OC.nc"
```
