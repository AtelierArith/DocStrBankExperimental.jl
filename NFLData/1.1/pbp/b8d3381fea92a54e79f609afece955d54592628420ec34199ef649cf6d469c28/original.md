```
load_participation(seasons = 2023, include_pbp::Bool = false)
```

**NOTICE:** The NFL limited the amount of participation data available publicly for the 2023 season, and ceased providing any data for the 2024 season. The 2023 season lacks complete coverage, and the 2024 season and future seasons are unlikely to ever be updated with data.

Load NGS participation data for a given season. Defaults to the 2023 season. Pass in `seasons = true` for all available seasons. To join this participation data to PBP data (as provided by `load_pbp()`), pass `include_pbp=true` into this function.

For information about this resource, see its data dictionary [here](https://nflreadr.nflverse.com/articles/dictionary_participation.html).
