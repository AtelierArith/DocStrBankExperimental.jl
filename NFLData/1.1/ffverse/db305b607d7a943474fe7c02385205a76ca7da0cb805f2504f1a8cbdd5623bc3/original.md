```
load_ff_rankings(type::AbstractString = "draft")
```

Load current fantasy football rankings from FantasyPros.com. The argument `type` has three valid parameters:

  * `"draft"`: FantasyPros rankings for draft leagues for the current fantasy football season. The default parameter.
  * `"week"`: FantasyPros rankings for players for the current week of the fantasy football season.
  * `"all"`: Historical FantasyPros rankings for a variety of formats.

For information about this resource, see its data dictionary [here](https://nflreadr.nflverse.com/articles/dictionary_ff_rankings.html).
