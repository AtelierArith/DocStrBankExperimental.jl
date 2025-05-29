```
IMERGFinalDY(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop  :: TimeType,
    path :: AbstractString = homedir(),
) -> npd :: IMERGDaily{ST,DT}
```

Creates a `IMERGDaily` dataset `npd` to retrieve datasets from the Final post-processing runs for Daily output

# Keyword Arguments

  * `start` : Date at which download / analysis of the dataset begins
  * `stop` : Date at which download / analysis of the dataset ends
  * `path` : The directory in which the folder `imergfinaldy` will be created for data downloads, storage and analysis, default is the home directoy called by `homedir()`

The following fields in `npd` will be fixed as below:

  * `ID` : imergfinaldy
  * `ID` : Final IMERG Daily
  * `doi`   : 10.5067/GPM/IMERGDF/DAY/06
  * `hroot` : https://gpm1.gesdisc.eosdis.nasa.gov/opendap/GPM*L3/GPM*3IMERGDF.06
  * `fpref` : 3B-DAY.MS.MRG.3IMERG
  * `fsuff` : S000000-E235959.V06.nc4
