```
struct PTC <: Policy
```

Production Tax Credit - A $/MWh tax incentive for the generation of specific technology or under specific conditions.

# Keyword Arguments

  * `name`: policy name
  * `values`: $/MWh values of the PTC, stored as an OrderedDict with years and the value `(:y2020=>10)`, note `year` is a `Symbol`
  * `years_after_ref_min`: Min (inclusive) number of years the sim year can be after gen reference year (ie. year*on, year*retrofit). If ref year is year_on then this would be equivaled to min gen age.
  * `years_after_ref_max`: Max (inclusive) number of years the sim year can be after gen reference year (ie. year*on, year*retrofit). If ref year is year_on then this would be equivaled to max gen age.
  * `ref_year_col`: Column name to use as reference year for min and max above. Must be a year column. If this is :year*on, then the years*after*ref filters will filter gen age. If this is :year*retrofit, the the years*after*ref filters will filter by time since retrofit.
  * `gen_filters`: filters for qualifying generators, stored as an OrderedDict with gen table columns and values (`:emis_co2=>"<=0.1"` for co2 emission rate less than or equal to 0.1)
