```
load_player_stats(stat_type::AbstractString = "offense")
```

Load stats for individual players as calculated from NFLFastR PBP data. Specify the type of stats returned by passing one of `"offense"`, `"defense"`, or `"kicking"` to `stat_type`.

For information about this resource, see the offensive stats data dictionary [here](https://nflreadr.nflverse.com/articles/dictionary_player_stats.html), and the defensive stats data dictionary [here](https://nflreadr.nflverse.com/articles/dictionary_player_stats_def.html).
