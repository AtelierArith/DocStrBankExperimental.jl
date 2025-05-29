```
struct EmissionPrice <: Policy
```

Emission Price - A price on a certain emission for a given set of generators.

  * `name`: name of the policy (Symbol)
  * `emis_col`: name of the emission rate column in the gen table (ie. emis_co2) (Symbol)
  * `prices`: OrderedDict of prices by year. Given as price per unit of emissions (ie. $/short ton)
  * `years_after_ref_min`: Min (inclusive) number of years the sim year can be after gen reference year (ie. year*on, year*retrofit). If ref year is year_on then this would be equivaled to min gen age. This is rarely used in real policy, so be careful if changing from default value
  * `years_after_ref_max`: Max (inclusive) number of years the sim year can be after gen reference year (ie. year*on, year*retrofit). If ref year is year_on then this would be equivaled to max gen age. This is rarely used in real policy, so be careful if changing from default value
  * `ref_year_col`: Column name to use as reference year for min and max above. Must be a year column. If this is :year*on, then the years*after*ref filters will filter gen age. If this is :year*retrofit, the the years*after*ref filters will filter by time since retrofit. This is rarely used in real policy, so be careful if changing from default value
  * `gen_filters`: OrderedDict of generator filters
  * `hour_filters`: OrderedDict of hour filters
