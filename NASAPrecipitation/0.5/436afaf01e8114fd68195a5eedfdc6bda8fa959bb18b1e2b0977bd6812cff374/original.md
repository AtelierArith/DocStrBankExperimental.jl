```
IMERGEarlyHH(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop  :: TimeType,
    path  :: AbstractString = homedir(),
) -> npd :: IMERGHalfHourly{ST,DT}
```

Creates a `IMERGHalfHourly` dataset `npd` to retrieve datasets from the Near Real-Time Early processing runs for Half-Hourly output

# Keyword Arguments

  * `start` : Date at which download / analysis of the dataset begins
  * `stop` : Date at which download / analysis of the dataset ends
  * `path` : The directory in which the folder `imergearlyhh` will be created for data downloads, storage and analysis, default is the home directoy called by `homedir()`

The following fields in `npd` will be fixed as below:

  * `ID` : imergearlyhh
  * `name` : Early IMERG Half-Hourly
  * `doi` : 10.5067/GPM/IMERG/3B-HH-E/06
  * `hroot` : https://gpm1.gesdisc.eosdis.nasa.gov/opendap/GPM*L3/GPM*3IMERGHHE.06
  * `fpref` : 3B-HHR-E.MS.MRG.3IMERG
  * `fsuff` : V06B.HDF5
