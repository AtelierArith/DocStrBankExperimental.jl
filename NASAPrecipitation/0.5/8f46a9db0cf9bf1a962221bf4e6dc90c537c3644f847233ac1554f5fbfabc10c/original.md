```
TRMM3HourlyNRT(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop  :: TimeType,
    path  :: AbstractString = homedir(),
) -> npd :: TRMM3Hourly{ST,DT}
```

Creates a `TRMM3Hourly` dataset `npd` to retrieve datasets from the Near Real-Time runs for 3-Hourly output

# Keyword Arguments

  * `start` : Date at which download / analysis of the dataset begins
  * `stop` : Date at which download / analysis of the dataset ends
  * `path` : The directory in which the folder `trmm3hourlynrt` will be created for data downloads, storage and analysis, default is the home directoy called by `homedir()`

The following fields in `npd` will be fixed as below:

  * `ID` : trmm3hourlynrt
  * `name` : Near Real-Time TRMM 3-Hourly
  * `doi`   : 10.5067/TRMM/TMPA/3H-E/7
  * `hroot` : https://disc2.gesdisc.eosdis.nasa.gov/opendap/TRMM*RT/TRMM*3B42RT.7
  * `fpref` : 3B42RT
  * `fsuff` : 7R2.nc4
