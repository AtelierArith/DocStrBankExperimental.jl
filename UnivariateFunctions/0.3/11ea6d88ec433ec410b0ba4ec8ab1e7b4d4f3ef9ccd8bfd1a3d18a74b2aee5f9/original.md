```
period_length(a::Dates.DatePeriod, base::Date = global_base_date)
```

Period length is designed to convert `TimePeriod` objects to a float in a consistent way to `years_from_global_base`. So effectively the years_between method is calculated with start and end dates being those at the start and end of a `Dates.DatePeriod`. This is slightly complicated because a period like `Month(3)` might have slightly different numbers of total days depending on when in the year it is. So a base date has to be input. The period is then measured starting from this base date.

### Inputs

  * `period` - A period.
  * `base` - A date from which the period will be measured from.

### Returns

  * A `Real`.
