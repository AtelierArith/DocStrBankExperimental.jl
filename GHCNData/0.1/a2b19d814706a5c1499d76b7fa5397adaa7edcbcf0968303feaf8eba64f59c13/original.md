```
load_station_metadata() -> DataFrame
```

Loads the station metadata detailed in section 4 of [1], returning it in a `DataFrame` with columns named according the the `Variable` column below:

```
------------------------------
Variable   Columns   Type
------------------------------
ID            1-11   Character
LATITUDE     13-20   Real
LONGITUDE    22-30   Real
ELEVATION    32-37   Real
STATE        39-40   Character
NAME         42-71   Character
GSN FLAG     73-75   Character
HCN/CRN FLAG 77-79   Character
WMO ID       81-85   Character
------------------------------
```

[1] - https://www1.ncdc.noaa.gov/pub/data/ghcn/daily/readme.txt
