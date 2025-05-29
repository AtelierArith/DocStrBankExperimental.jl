```
get_carbon_intensity(start_date::ZonedDateTime, end_date::ZonedDateTime)
```

Returns a NamedTuple with two fields named `intensity` and `generation`. Both tables contain data spanning the period defined by the `start_date` and `end_date`. the `intensity` field contains a dataframe of the forecast data of the regional carbon intensity, and the `generation` field contains a dataframe of the regional generation as a percent of the total generation.
