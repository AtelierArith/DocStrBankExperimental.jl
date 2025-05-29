```
function load_ff_opportunity(seasons::Number = most_recent_season(), stat_type::AbstractString = "weekly", model_version::AbstractString = "latest")
```

Load the FFOpportunity dataset for a given season. `seasons` indicates the years to pull data from and defaults to the most recently played NFL season. Pass in `seasons = true` for all available seasons. `stat_type` takes three potential arguments:

  * `"weekly"`: Pull full FFOpportunity data, week by week. The default option.
  * `"pbp_pass"`: Pull full FFOpportunity passing data, week by week.
  * `"pbp_rush"`: Pull full FFOpportunity rushing data, week by week.

`model_version` takes two potential arguments:

  * `"latest"`: Pull data produced by the latest FFOpportunity models.
  * `"v1.0.0"`: Pull data produced by the original FFOpportunity models.

For information about this resource, see its data dictionary [here](https://nflreadr.nflverse.com/articles/dictionary_ff_opportunity.html).
