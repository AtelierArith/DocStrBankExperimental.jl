```
IMERGMonthly(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop  :: TimeType,
    path  :: AbstractString = homedir(),
) -> npd :: IMERGMonthly{ST,DT}
```

Creates a `IMERGMonthly` dataset `npd` to retrieve datasets for Monthly output

# Keyword Arguments

  * `start` : Date at which download / analysis of the dataset begins
  * `stop` : Date at which download / analysis of the dataset ends
  * `path` : The directory in which the folder `imergmonthly` will be created for data downloads, storage and analysis, default is the home directoy called by `homedir()`

The following fields in `npd` will be fixed as below:

  * `ID` : imergmonthly
  * `name` : IMERG Monthly
  * `doi` : 10.5067/GPM/IMERG/3B-MONTH/06
  * `hroot` : https://gpm1.gesdisc.eosdis.nasa.gov/opendap/GPM*L3/GPM*3IMERGM.06
  * `fpref` : 3B-MO.MS.MRG.3IMERG
  * `fsuff` : V06B.HDF5
