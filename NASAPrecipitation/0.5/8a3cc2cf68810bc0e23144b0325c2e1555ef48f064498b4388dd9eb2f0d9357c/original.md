```
IMERGLateHH(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop :: TimeType,
    path :: AbstractString = homedir(),
) -> npd :: IMERGHalfHourly{ST,DT}
```

Creates a `IMERGHalfHourly` dataset `npd` to retrieve datasets from the Near Real-Time Late processing runs for Half-Hourly output

# Keyword Arguments

  * `start` : Date at which download / analysis of the dataset begins
  * `stop` : Date at which download / analysis of the dataset ends
  * `path` : The directory in which the folder `imerglatehh` will be created for data downloads, storage and analysis, default is the home directoy called by `homedir()`

The following fields in `npd` will be fixed as below:

  * `ID` : imerglatehh
  * `name` : Late IMERG Half-Hourly
  * `doi`   : 10.5067/GPM/IMERG/3B-HH-L/06
  * `hroot` : https://gpm1.gesdisc.eosdis.nasa.gov/opendap/GPM*L3/GPM*3IMERGHHL.06
  * `fpref` : 3B-HHR-L.MS.MRG.3IMERG
  * `fsuff` : V06B.HDF5
