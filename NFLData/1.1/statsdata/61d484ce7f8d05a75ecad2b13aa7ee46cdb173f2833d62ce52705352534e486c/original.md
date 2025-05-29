```
load_pfr_advstats(seasons = most_recent_season(), stat_type::String = "pass", summary_level::String = "week")
```

Load advanced stats from [Pro-Football-Reference.com](https://www.pro-football-reference.com/) for a given season. Defaults to the most recent season. Pass in `seasons = true` for all available seasons.

Specify the types of stats returned by passing one of `"pass"`,`"rush"`,`"rec"`, or `"def"` to `stat_type`.

Specify the summary level of stats returned by passing one of `"week"` or `"season"` to `summary_level`.

For information about this resource, see its data dictionary [here](https://nflreadr.nflverse.com/articles/dictionary_pfr_passing.html).
