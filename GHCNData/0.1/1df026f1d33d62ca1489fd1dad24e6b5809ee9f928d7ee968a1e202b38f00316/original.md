```
load_inventories() -> DataFrame
```

Loads the inventory file detailed in section 7 of [1], and returns a `DataFrame` with columns named according to the variables listed in the file-format information below.

```
------------------------------
Variable   Columns   Type
------------------------------
ID            1-11   Character
LATITUDE     13-20   Real
LONGITUDE    22-30   Real
ELEMENT      32-35   Character
FIRSTYEAR    37-40   Integer
LASTYEAR     42-45   Integer
------------------------------
```

[1] - https://www1.ncdc.noaa.gov/pub/data/ghcn/daily/readme.txt
