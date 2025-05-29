```
TRMMDaily(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop  :: TimeType,
    path  :: AbstractString = homedir(),
) -> npd :: TRMMDaily{ST,DT}
```

Creates a `TRMMDaily` dataset `npd` to retrieve datasets from the Final post-processing runs for Daily output

# Keyword Arguments

  * `start` : Date at which download / analysis of the dataset begins
  * `stop` : Date at which download / analysis of the dataset ends
  * `path` : The directory in which the folder `trmmdaily` will be created for data downloads, storage and analysis, default is the home directoy called by `homedir()`

The following fields in `npd` will be fixed as below:

  * `ID` : trmmdaily
  * `name` : Final TRMM Daily
  * `doi` : 10.5067/TRMM/TMPA/DAY/7
  * `hroot` : https://disc2.gesdisc.eosdis.nasa.gov/opendap/TRMM*L3/TRMM*3B42_Daily.7
  * `fpref` : 3B42_Daily
  * `fsuff` : 7.nc4
