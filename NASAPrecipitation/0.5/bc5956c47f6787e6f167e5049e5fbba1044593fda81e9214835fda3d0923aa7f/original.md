```
TRMMMonthly(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop  :: TimeType,
    path  :: AbstractString = homedir(),
) -> npd :: TRMMMonthly{ST,DT}
```

Creates a `TRMMMonthly` dataset `npd` to retrieve datasets from the Final post-processing runs for Monthly output

# Keyword Arguments

  * `start` : Date at which download / analysis of the dataset begins
  * `stop` : Date at which download / analysis of the dataset ends
  * `path` : The directory in which the folder `trmmmonthly` will be created for data downloads, storage and analysis, default is the home directoy called by `homedir()`

The following fields in `npd` will be fixed as below:

  * `ID` : trmmmonthly
  * `name` : TRMM Monthly (TMPA 3B43)
  * `doi` : 10.5067/TRMM/TMPA/MONTH/7
  * `hroot` : https://disc2.gesdisc.eosdis.nasa.gov/opendap/TRMM*L3/TRMM*3B43.7
  * `fpref` : 3B43
  * `fsuff` : 7.HDF
