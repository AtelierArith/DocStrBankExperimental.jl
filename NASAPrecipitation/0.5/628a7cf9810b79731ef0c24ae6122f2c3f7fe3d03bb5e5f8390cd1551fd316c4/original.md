```
IMERGFinalHH(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop :: TimeType,
    path :: AbstractString = homedir(),
) -> npd :: IMERGHalfHourly{ST,DT}
```

Creates a `IMERGHalfHourly` dataset `npd` to retrieve datasets from the final post-processing runs for Half-Hourly output

# Keyword Arguments

  * `start` : Date at which download / analysis of the dataset begins
  * `stop` : Date at which download / analysis of the dataset ends
  * `path` : The directory in which the folder `imergfinalhh` will be created for data downloads, storage and analysis, default is the home directoy called by `homedir()`

The following fields in `npd` will be fixed as below:

  * `ID` : imergfinalhh
  * `name` : Final IMERG Half-Hourly
  * `doi`   : 10.5067/GPM/IMERG/3B-HH/06
  * `hroot` : https://gpm1.gesdisc.eosdis.nasa.gov/opendap/GPM*L3/GPM*3IMERGHH.06
  * `fpref` : 3B-HHR.MS.MRG.3IMERG
  * `fsuff` : V06B.HDF5
