```
load_station_metadata() -> DataFrame
```

セクション4の[1]に詳述されている駅のメタデータを読み込み、以下の`Variable`列に従って名前が付けられた列を持つ`DataFrame`として返します：

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
